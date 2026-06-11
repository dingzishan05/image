# 文字/编号转二维码 Spec

## Why
当前项目仅支持将 URL 链接生成二维码。用户需要扩展功能，支持将任意文字、编号等纯文本内容也生成为二维码，方便通过扫码快速传递文本信息。

## What Changes
- 页面标题和文案从"URL 转二维码"更新为更通用的表述，支持文字和 URL 两种输入
- 新增输入模式切换：URL 模式和文字模式，用户可选择输入类型
- 保留现有 URL 输入和生成二维码的全部功能
- 文字模式下不对内容做 URL 校验，允许任意文本/编号输入
- GitHub 仓库地址：`https://github.com/dingzishan05/image`

## Impact
- Affected specs: 无（新增功能）
- Affected code: `index.html`（UI 和 JS 逻辑修改）

## ADDED Requirements

### Requirement: 文字/编号生成二维码
系统 SHALL 支持用户输入任意文字或编号，并将其生成二维码。

#### Scenario: 输入文字生成二维码
- **WHEN** 用户选择"文字"模式，输入一段文字（如"会议室A"）
- **THEN** 系统将该文字生成对应的二维码并显示

#### Scenario: 输入编号生成二维码
- **WHEN** 用户选择"文字"模式，输入一个编号（如"SN20240601001"）
- **THEN** 系统将该编号生成对应的二维码并显示

### Requirement: 输入模式切换
系统 SHALL 提供 URL 和文字两种输入模式，用户可自由切换。

#### Scenario: 切换到文字模式
- **WHEN** 用户点击"文字"模式标签
- **THEN** 输入框提示语变更为文字输入相关的提示（如"输入文字或编号"），且不使用 URL 校验逻辑

#### Scenario: 切换到 URL 模式
- **WHEN** 用户点击"URL"模式标签
- **THEN** 输入框提示语变更为 URL 输入提示（如"输入链接"），行为与现有功能一致

### Requirement: 二维码下方显示原始内容
系统 SHALL 在二维码下方显示用户输入的内容原文。

#### Scenario: 显示文字内容
- **WHEN** 用户在文字模式下生成二维码
- **THEN** 二维码下方显示输入的文字原文，不做链接展示

## MODIFIED Requirements

### Requirement: 页面标题与整体风格
页面标题从"URL 转二维码"更新为"二维码生成器"，UI 风格保持一致。

#### Scenario: 页面加载
- **WHEN** 用户打开页面
- **THEN** 页面标题显示"二维码生成器"，默认选中"URL"模式
