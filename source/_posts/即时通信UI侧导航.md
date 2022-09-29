---
title: React 即时通信 UI 侧导航
date: 2022-09-29
tags: [React]
categories: Web前端
references: 
  - title: React 即时通信 UI 实战
    url: https://study.163.com/course/courseMain.htm?courseId=1210022809&share=1&shareId=1030428673
---

> React 即时通信 UI 实战第三章。React 即时通信 UI 实战为[峰华前端工程师](https://www.bilibili.com/video/BV1PK4y1b7bY?p=2&spm_id_from=pageDriver&vd_source=0965c74096f788f105780e5d5d0e9ebf)推出的 React 实战课程，以聊天（即时通信）为原型，构建了一整套的 UI 组件库，课程重点在于 UI 组件的分析和实现，力求打造自用组件库。本章包括侧导航中的头像、菜单项等组件。

<!--more-->

### 一、头像组件

在 `src` 目录下新建 `components/Avatar` 两级文件夹，用于存放组件的定义。文件夹中一般有 `index.js`（组件主体代码）、`style.js`（Styled-components 样式组件代码）、`组件名.stories.js`（组件 stories）、`hook.js`（自定义的 hooks）文件。

在 `index.js` 文件中快捷输入 `rfcp + tab`（reactFunctionalComponentWithPropTypes）导入依赖、创建一个函数式组件、引入propTypes：

```js
import React from 'react'
import PropTypes from 'prop-types'
import face1 from "../../assets/images/face-male-1.jpg";
import StyledAvatar, { StatusIcon, AvatarClip, AvatarImage } from "./style";

function Avatar({ src, size = "48px", status, statusIconSize = "8px", ...rest }) {
    return (
        <StyledAvatar {...rest}>
            {status && <StatusIcon status={status} size={statusIconSize}></StatusIcon>}
            <AvatarClip size={size}>
                <AvatarImage src={src} alt="" />
            </AvatarClip>
        </StyledAvatar>
    )
}

Avatar.propTypes = {
    src: PropTypes.string.isRequired,
    size: PropTypes.string,
    status: PropTypes.oneOf(["online", "offline"]),
    statusIconSize: PropTypes.string,
}

export default Avatar;
```

在 `Avatar` 目录下新建 `avatar.stories.js` 文件：

```js
import React from "react";
import Avatar from ".";
import face1 from "../../assets/images/face-male-1.jpg";
import face2 from "../../assets/images/face-male-2.jpg";
import face3 from "../../assets/images/face-male-3.jpg";
import face4 from "../../assets/images/face-male-4.jpg";

import "../../story.css"

export default {
    title: "Avatar",
    component: Avatar,
}

export const Default = () => {
    return <Avatar src={face1} />
}

export const Sizes = () => {
    return (
        <div className="row-elements">
            <Avatar src={face1} size="48px" />
            <Avatar src={face2} size="56px" />
            <Avatar src={face3} size="64px" />
            <Avatar src={face4} size="72px" />
        </div>
    );
};

export const WithStatus = () => {
    return (
        <div className="row-elements">
            <Avatar src={face1} status="online" />
            <Avatar src={face2} status="offline" />
            <Avatar src={face4} status="offline" size="72px" statusIconSize="12px" />
        </div>
    );
};
```

在 `Avatar` 目录下新建 `style.js` 文件：

```js
import styled, { css } from 'styled-components';

const circleMixinFunc = (color, size = "8px") => css`
    content: "";
        display: block;
        position: absolute;
        width: ${size};
        height: ${size};
        border-radius: 50%;
        background-color: ${color};
`;

const StyledAvatar = styled.div`
    position: relative;
`;

const StatusIcon = styled.div`
    position: absolute;
    left: 2px;
    top: 4px;

    &::before {
        ${({ size }) => circleMixinFunc("white", size)}
        transform: scale(2);
    }

    &::after {
        ${({ theme, status, size }) => {
        if (status === "online") {
            return circleMixinFunc(theme.green, size);
        } else if (status === "offline") {
            return circleMixinFunc(theme.gray, size);
        }
    }}
    }
`;

const AvatarClip = styled.div`
    width: ${({ size }) => size};
    height: ${({ size }) => size};
    border-radius: 50%;
    overflow: hidden;
`;

const AvatarImage = styled.img`
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
`;

export default StyledAvatar;
export { StatusIcon, AvatarClip, AvatarImage };
```

### 二、jsconfig.json 文件

在 ChatUI 项目根目录下创建 `jsconfig.json` 项目配置文件：

```json
{
    "compilerOptions": {
      "baseUrl": "src"
    },
    "include": ["src"],
    "exclude": ["node_modules", "**/node_modules/*"]
}
```

此时，在 `avatar.stories.js` 文件中导入可用相对路径导入：

```js
import face1 from "assets/images/face-male-1.jpg";
import face2 from "assets/images/face-male-2.jpg";
import face3 from "assets/images/face-male-3.jpg";
import face4 from "assets/images/face-male-4.jpg";
import "story.css"
```

