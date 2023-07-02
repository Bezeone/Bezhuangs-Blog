---
title: ChatUI-React 内容区
date: 2022-10-15
tags: [ChatUI]
categories: Front-End Development
references: 
  - title: React 即时通信 UI 实战
    url: https://study.163.com/course/courseMain.htm?courseId=1210022809&share=1&shareId=1030428673
---

> React 即时通信 UI 实战第六章。React 即时通信 UI 实战为[峰华前端工程师](https://www.bilibili.com/video/BV1PK4y1b7bY?p=2&spm_id_from=pageDriver&vd_source=0965c74096f788f105780e5d5d0e9ebf)推出的 React 实战课程，以聊天（即时通信）为原型，构建了一整套的 UI 组件库，课程重点在于 UI 组件的分析和实现，力求打造自用组件库。本章包括内容区中的标题栏、会话气泡、会话窗口、语音消息等组件。以下为我在学习和实战练习过程中所做的笔记，可供参考。

<!--more-->

### 一、标题栏组件开发

使用 Hygen 创建一个标题栏组件：

```bash
hygen component new TitleBar
```

在 `index.js` 文件中编辑标题栏组件：

```JS
import React from "react";
import PropTypes from "prop-types";
import StyledTitleBar, { Actions, Title } from "./style";
import Avatar from "components/Avatar";
import Paragraph from "components/Paragraph";
import Text from "components/Text";
import Icon from "components/Icon";

import face from "assets/images/face-male-3.jpg";
import { ReactComponent as Call } from "assets/icon/call.svg";
import { ReactComponent as Camera } from "assets/icon/camera.svg";
import { ReactComponent as Options } from "assets/icon/options.svg";

function TitleBar({ children, ...rest }) {
  return (
    <StyledTitleBar {...rest}>
      <Avatar status="offline" src={face} />
      <Title>
        <Paragraph size="large">慕容天宇</Paragraph>
        <Paragraph type="secondary">
          <Text>离线</Text>
          <Text>· 最后阅读：3小时前</Text>
        </Paragraph>
      </Title>
      <Actions>
        <Icon opacity={0.3} icon={Call} />
        <Icon opacity={0.3} icon={Camera} />
        <Icon opacity={0.3} icon={Options} />
      </Actions>
    </StyledTitleBar>
  );
}

TitleBar.propTypes = {
  children: PropTypes.any
};

export default TitleBar;
```

再在 `style.js` 中修改样式，使用 Grid 布局：

```JS
import StyledIcon from "components/Icon/style";
import styled from "styled-components";

const Title = styled.div`
    display: grid;
`;

const Actions = styled.div`
    display: flex;
    justify-content: space-between;
    align-items: center;
    ${StyledIcon} {
        cursor: pointer;
    }
`;

const StyledTitleBar = styled.div`
    display: grid;
    grid-template-columns: 62px 1fr 112px;
    padding: 30px;
    max-height: 110px;
    border-bottom: 1px solid ${({ theme }) => theme.gray4};
`;

export default StyledTitleBar;
export { Actions, Title };
```

最后编辑 `titleBar.stories.js` 文件：

```JS
import React from "react";
import TitleBar from ".";

export default {
  title: "UI 组件/TitleBar",
  component: TitleBar,
};

export const Default = () => <TitleBar />;
```

### 二、会话气泡组件开发

会话气泡用于突出显示聊天的内容，使用 Hygen 创建一个标题栏组件：

```bash
hygen component new ChatBubble
```

在 `index.js` 文件中编辑会话气泡组件：

```JS
import React from "react";
import PropTypes from "prop-types";
import StyledChatBubble, { Bubble, BubbleTip, Time, MessageText, } from "./style";

import { ReactComponent as BubbleTipIcon } from "assets/icon/bubbleTip.svg";

function ChatBubble({ children, type, time, ...rest }) {
  return (
    <StyledChatBubble type={type} {...rest}>
      <Bubble>
        <BubbleTip icon={BubbleTipIcon} width={40} height={28} color="white" />
        <MessageText>{children}</MessageText>
      </Bubble>
      <Time>{time}</Time>
    </StyledChatBubble>
  );
}

ChatBubble.propTypes = {
  children: PropTypes.any,
  type: PropTypes.oneOf(["mine"]),
  time: PropTypes.string,
};

export default ChatBubble;
```

再在 `style.js` 中修改样式：

```JS
import styled, { css } from "styled-components";
import Paragraph from "components/Paragraph";
import Icon from "components/Icon";
import Text from "components/Text";

const Time = styled(Paragraph).attrs({ type: "secondary", size: "small" })`
    margin: 6px;
    margin-left: 24px;
    word-spacing: 1rem;
`;

const BubbleTip = styled(Icon)`
    position: absolute;
    bottom: -15%;
    left: 0;
    z-index: 5;
`;

const Bubble = styled.div`
    padding: 15px 22px;
    box-shadow: 0px 8px 24px rgba(0, 0, 0, 0.1);
    border-radius: 100px;
    position: relative;
    z-index: 10;
`;

const MessageText = styled(Text)``;

const typeVariants = {
    mine: css`
      ${Bubble} {
        background-color: ${({ theme }) => theme.primaryColor};
      }
  
      ${BubbleTip} {
        transform: rotateY(180deg);
        left: unset;
        right: 0;
  
        path {
          fill: ${({ theme }) => theme.primaryColor};
        }
      }
  
      ${Time} {
        text-align: right;
        margin-left: 0;
        margin-right: 24px;
      }
  
      ${MessageText} {
        color: white;
      }
    `,
};

const StyledChatBubble = styled.div`
    display: flex;
    flex-direction: column;
    ${({ type }) => type && typeVariants[type]}
`;

export default StyledChatBubble;
export { Bubble, BubbleTip, Time, MessageText };
```

最后编辑 `chatBubble.stories.js` 文件，使用 decorators 设置 stories 中默认边距：

```JS
import React from "react";
import ChatBubble from ".";

export default {
  title: "UI 组件/ChatBubble",
  component: ChatBubble,
  decorators: [(storyFn) => <div style={{ padding: "24px" }}>{storyFn()}</div>]
};

export const FromOthers = () => (
  <ChatBubble time="昨天 下午14：26">这是一条其它人发送的聊天消息</ChatBubble>
);

export const Mine = () => (
  <ChatBubble type="mine" time="昨天 下午16：30">
    这是一条我自己发送的聊天消息
  </ChatBubble>
);
```

### 三、语音消息组件开发

使用 Hygen 创建一个语音消息组件：

```bash
hygen component new VoiceMessage
```

在 `index.js` 文件中编辑语音消息组件：

```JS
import React from "react";
import PropTypes from "prop-types";
import StyledVoiceMessage from "./style";

import { ReactComponent as Play } from "assets/icon/play.svg";
import { ReactComponent as Wave } from "assets/icon/wave.svg";
import { useTheme } from "styled-components";
import Button from "components/Button";
import Icon from "components/Icon";
import Text from "components/Text";

function VoiceMessage({ children, time, type, ...rest }) {
  const theme = useTheme();
  return (
    <StyledVoiceMessage type={type} {...rest}>
      <Button size="40px">
        <Icon icon={Play} color="white" width="14" height="16" style={{ transform: "translateX(1px)" }} />
      </Button>
      <Icon icon={Wave} width="100%" height="100%" color={theme.primaryColor} />
      <Text bold>{time}</Text>
    </StyledVoiceMessage>
  );
}

VoiceMessage.propTypes = {
  children: PropTypes.any,
  type: PropTypes.oneOf(["mine"]),
  time: PropTypes.string,
};

export default VoiceMessage;
```

再在 `style.js` 中修改样式：

```JS
import styled, { css } from "styled-components";
import StyledButton from "components/Button/style";
import StyledIcon from "components/Icon/style";
import StyledText from "components/Text/style";

const typeVariants = {
    mine: css`
    ${StyledButton} {
      background-color: white;

      ${StyledIcon} path {
        fill: ${({ theme }) => theme.primaryColor};
      }
    }
    & > ${StyledIcon} path {
      fill: white;
    }

    & > ${StyledText} {
      color: white;
    }
  `,
};

const StyledVoiceMessage = styled.div`
  display: flex;
  align-items: center;

  & > *:first-child {
    flex-shrink: 0;
  }

  & > *:not(:first-child) {
    margin-left: 16px;
  }

  ${({ type }) => type && typeVariants[type]}
`;

export default StyledVoiceMessage;
```

编辑 `voiceMessage.stories.js` 文件：

```JS
import React from "react";
import VoiceMessage from ".";

export default {
  title: "UI 组件/VoiceMessage",
  component: VoiceMessage,
};

export const Default = () => <VoiceMessage time="01:25" />;
```

最后将语音条添加到会话气泡中，编辑 `chatBubble.stories.js` 文件：

```JS
import VoiceMessage from "components/VoiceMessage";
import React from "react";
import ChatBubble from ".";

export default {
  title: "UI 组件/ChatBubble",
  component: ChatBubble,
  decorators: [(storyFn) => <div style={{ padding: "24px" }}>{storyFn()}</div>]
};

export const FromOthers = () => (
  <ChatBubble time="昨天 下午14：26">这是一条其它人发送的聊天消息</ChatBubble>
);

export const Mine = () => (
  <ChatBubble type="mine" time="昨天 下午16：30">
    这是一条我自己发送的聊天消息
  </ChatBubble>
);

export const VoiceMessageType = () => (
  <ChatBubble time="昨天 下午18：30">
    <VoiceMessage time="01:24" />
  </ChatBubble>
);

export const VoiceMessageTypeMine = () => (
  <ChatBubble type="mine" time="昨天 下午18：30">
    <VoiceMessage type="mine" time="01:24" />
  </ChatBubble>
);
```

### 四、Emoji 组件开发

Emoji 组件用来显示表情，可以直接使用操作系统自带表情，再用 React 封装，根据可访问原则，Emoji 应用 `span` 标签包装，并设置 `role` 和 `aria-label` 属性：

```html
<span role="img" aria-label="smirk">😜</span>
```

使用 Hygen 创建一个 Emoji 组件：

```bash
hygen component new Emoji
```

在 `index.js` 文件中编辑标题栏组件：

```JS
import React from "react";
import PropTypes from "prop-types";
import StyledEmoji from "./style";

function Emoji({ children, label, ...rest }) {
  return (
    <StyledEmoji role="img" aria-label={label} {...rest}>
      {children}
    </StyledEmoji>
  );
}

Emoji.propTypes = {
  children: PropTypes.any,
  label: PropTypes.string,
};

export default Emoji;
```

再在 `style.js` 中修改样式，使用 span 渲染：

```JS
import styled from "styled-components";

const StyledEmoji = styled.span``;

export default StyledEmoji;
```

编辑 `emoji.stories.js` 文件：

```JS
import React from "react";
import Emoji from ".";

export default {
  title: "UI 组件/Emoji",
  component: Emoji,
};

/* eslint-disable jsx-a11y/accessible-emoji */
export const Default = () => (
  <div>
    <Emoji label="smile">😄</Emoji>
    <Emoji label="todo">✅</Emoji>
    <Emoji label="clock">🕔</Emoji>
  </div>
);
```

最后编辑 `chatBubble.stories.js` 文件，给 Mine 输入添加笑脸 Emoji：

```JS
import Emoji from "components/Emoji";

/* eslint-disable jsx-a11y/accessible-emoji */
export const Mine = () => (
  <ChatBubble type="mine" time="昨天 下午16：30">
    这是一条我自己发送的聊天消息<Emoji label="smile">😄</Emoji>
  </ChatBubble>
);
```

### 五、Popover 组件开发

弹出层组件 Popover 用于显示额外的弹出层，使用 Hygen 创建一个弹出层组件：

```bash
hygen component new Popover
```

在 `index.js` 文件中编辑标题栏组件：

```JS
import React, { useState } from "react";
import PropTypes from "prop-types";
import StyledPopover, { Content, Triangle, Target } from "./style";

function Popover({ children, content, offset = {}, onVisible, onHide, ...rest }) {
  const [visible, setVisible] = useState(false);

  const handleClick = () => {
    if (visible) {
      setVisible(false);
      onHide && onHide();
    } else {
      setVisible(true);
      onVisible && onVisible();
    }
  };

  return (
    <StyledPopover onClick={handleClick} {...rest}>
      <Content visible={visible} offset={offset}>
        {content}
      </Content>
      <Triangle visible={visible} offset={offset} />
      <Target>{children}</Target>
    </StyledPopover>
  );
}

Popover.propTypes = {
  children: PropTypes.any,
  content: PropTypes.any,
  offset: PropTypes.shape({ x: PropTypes.string, y: PropTypes.string }),
  onVisible: PropTypes.func,
  onHide: PropTypes.func,
};

export default Popover;
```

再在 `style.js` 中修改样式：

```JS
import styled from "styled-components";

const Content = styled.div`
  background: ${({ theme }) => theme.background};
  border-radius: 21px;
  box-shadow: 0px 8px 40px rgba(0, 0, 0, 0.12);
  padding: 12px 30px;
  position: absolute;

  bottom: calc(100% + 12px);

  ${({ offset }) =>
    offset && `transform: translate(${offset.x || 0}, ${offset.y || 0})`};
  ${({ visible }) => !visible && `display: none`};
`;

const Triangle = styled.div`
  position: absolute;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 6px 6px 0 6px;
  border-color: ${({ theme }) => theme.background} transparent transparent
    transparent;
  left: calc(50% - 6px);
  bottom: calc(100% + 12px - 5px);

  ${({ offset }) => offset && `transform: translateY(${offset.y || 0});`}
  ${({ visible }) => !visible && `display: none`};
`;

const Target = styled.div``;

const StyledPopover = styled.div`
  display: flex;
  justify-content: center;
  position: relative;
`;

export default StyledPopover;
export { Content, Target, Triangle };
```

最后编辑 `popover.stories.js` 文件：

```JS
import React from "react";
import Popover from ".";
import Button from "components/Button";

export default {
  title: "UI 组件/Popover",
  component: Popover,
};

export const Default = () => (
  <div
    style={{
      display: "flex",
      justifyContent: "center",
      alignItems: "center",
      height: "50vh",
    }}
  >
    <Popover content="Hello!">
      <Button shape="rect">点我</Button>
    </Popover>
  </div>
);

export const WithOffset = () => (
  <div
    style={{
      display: "flex",
      justifyContent: "center",
      alignItems: "center",
      height: "50vh",
    }}
  >
    <Popover offset={{ x: "-25%" }} content={"Hello!"}>
      <Button shape="rect">点我</Button>
    </Popover>
  </div>
);
```

### 六、底部操作组件开发

使用 Hygen 创建一个底部操作组件：

```bash
hygen component new Footer
```

在 `index.js` 文件中编辑标题栏组件：

```JS
import React, { useState } from "react";
import PropTypes from "prop-types";
import StyledFooter, { IconContainer, StyledPopoverContent } from "./style";

import { ReactComponent as ClipIcon } from "assets/icon/clip.svg";
import { ReactComponent as SmileIcon } from "assets/icon/smile.svg";
import { ReactComponent as MicrophoneIcon } from "assets/icon/microphone.svg";
import { ReactComponent as PlaneIcon } from "assets/icon/plane.svg";
import { ReactComponent as OptionsIcon } from "assets/icon/options.svg";
import Input from "components/Input";
import Icon from "components/Icon";
import Button from "components/Button";
import Emoji from "components/Emoji";
import Popover from "components/Popover";
import { useTheme } from "styled-components";

function Footer({ animeProps, style, children, ...rest }) {
  const [emojiIconActive, setEmojiIconActive] = useState(false);
  const theme = useTheme();
  return (
    <StyledFooter style={{ ...style, ...animeProps }} {...rest}>
      <Input
        placeholder="输入想和对方说的话"
        prefix={<Icon icon={ClipIcon} />}
        suffix={
          <IconContainer>
            <Popover
              content={<PopoverContent />}
              offset={{ x: "-25%" }}
              onVisible={() => setEmojiIconActive(true)}
              onHide={() => setEmojiIconActive(false)}
            >
              <Icon
                icon={SmileIcon}
                color={emojiIconActive ? undefined : theme.gray3}
              />
            </Popover>
            <Icon icon={MicrophoneIcon} />
            <Button size="52px">
              <Icon
                icon={PlaneIcon}
                color="white"
                style={{ transform: "translateX(-2px)" }}
              />
            </Button>
          </IconContainer>
        }
      />
    </StyledFooter>
  );
}

/* eslint-disable jsx-a11y/accessible-emoji */
function PopoverContent(props) {
  return (
    <StyledPopoverContent>
      <Emoji label="smile">😊</Emoji>
      <Emoji label="grinning">😆</Emoji>
      <Emoji label="thumbup">👍</Emoji>
      <Emoji label="indexfingerup">☝️</Emoji>
      <Emoji label="ok">👌</Emoji>
      <Emoji label="handsputtogether">🙏</Emoji>
      <Emoji label="smilewithsunglasses">😎</Emoji>
      <Emoji label="flexedbicep">💪</Emoji>
      <Icon icon={OptionsIcon} style={{ marginLeft: "24px" }} />
    </StyledPopoverContent>
  );
}

Footer.propTypes = {
  children: PropTypes.any,
};

export default Footer;
```

再在 `style.js` 中修改样式：

```JS
import styled from "styled-components";

const IconContainer = styled.div`
  display: flex;
  align-items: center;
  margin-right: -30px;
  & > * {
    margin-left: 16px;
  }
`;

const StyledPopoverContent = styled.div`
  display: flex;
  & > * {
    margin: 0 8px;
    font-size: 16px;
  }
`;

const StyledFooter = styled.footer`
  padding: 12px 30px;
  width: 100%;
`;

export default StyledFooter;
export { IconContainer, StyledPopoverContent };
```

最后编辑 `footer.stories.js` 文件：

```JS
import React from "react";
import Footer from ".";

export default {
  title: "页面组件/Footer",
  component: Footer,
};

export const Default = () => (
  <div style={{ marginTop: 80 }}>
    <Footer />
  </div>
);
```

### 七、会话窗口组件开发

最后，将以上编写的所有组件组装起来，使用 Hygen 创建一个会话窗口组件：

```bash
hygen component new Conversation
```

在 `index.js` 文件中编辑标题栏组件：

```JS
import React from "react";
import PropTypes from "prop-types";
import StyledConversation, { Conversations, MyChatBubble } from "./style";
import TitleBar from "components/TitleBar";
import ChatBubble from "components/ChatBubble";
import VoiceMessage from "components/VoiceMessage";
import Emoji from "components/Emoji";
import Footer from "components/Footer";

function Conversation({ children, ...rest }) {
  return (
    <StyledConversation {...rest}>
      <TitleBar />
      <Conversations>
        <ChatBubble time="昨天 下午14：26">Hi 小宇，忙什么呢？</ChatBubble>
        <MyChatBubble time="昨天 下午16：30">
          Hello 啊！最近就是一直在加班改 bug，然后 怼产品，怼 UI，各种怼！
        </MyChatBubble>
        <ChatBubble time="昨天 下午18：30">
          <VoiceMessage time="01:24" />
        </ChatBubble>
        <MyChatBubble time="昨天 下午16：30">
          明天约一把王者荣耀，不连赢5把不罢休 🤘
          <Emoji label="smile">🤘</Emoji>
        </MyChatBubble>
      </Conversations>
      <Footer />
    </StyledConversation>
  );
}

Conversation.propTypes = {
  children: PropTypes.any
};

export default Conversation;
```

再在 `style.js` 中修改样式：

```JS
import ChatBubble from "components/ChatBubble";
import styled from "styled-components";

const Conversations = styled.div`
  padding: 10px 15px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 100%;
  overflow-y: auto;
  flex: 1;

  & > * {
    margin: 10px 0;
  }
`;

const MyChatBubble = styled(ChatBubble).attrs({ type: "mine" })`
  align-self: flex-end;
`;

const StyledConversation = styled.div`
  display: flex;
  flex-direction: column;
  height: 100vh;
  border: 1px solid ${({ theme }) => theme.gray4};

  & > *:last-child {
    align-self: end;
  }
`;

export default StyledConversation;
export { Conversations, MyChatBubble };
```

最后编辑 `popover.stories.js` 文件：

```JS
import React from "react";
import Conversation from ".";

export default {
  title: "页面组件/Conversation",
  component: Conversation,
};

export const Default = () => <Conversation />;
```
