---
title: MSBuild 参考C++Visual Studio 中的项目
ms.date: 12/08/2018
helpviewer_keywords:
- MSBuild reference [C++]
ms.openlocfilehash: b6ec6b5d276cb7104cf61c229476596d2a2a7684
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320924"
---
# <a name="msbuild-reference-for-c-projects"></a>MSBuild 参考C++项目

MSBuild 是 Visual Studio 中的所有项目的本机生成系统包括C++项目。 Visual Studio 集成的开发环境 (IDE) 中的项目生成时，它调用了 msbuild.exe 工具，它又使用.vcxproj 项目文件中和各种.targets 和.props 文件。 一般情况下，我们强烈建议使用 Visual Studio IDE 设置项目属性以及调用 MSBuild。 手动编辑项目文件可能导致严重问题，如果操作不正确。

如果出于某种原因，你想要直接从命令行使用 MSBuild，请参阅[从命令行使用 MSBuild](../msbuild-visual-cpp.md)。 有关 MSBuild 的详细信息一般情况下，请参阅[MSBuild](/visualstudio/msbuild/msbuild) Visual Studio 文档中。

## <a name="in-this-section"></a>本节内容

[C++ 项目的 MSBuild 内部项](msbuild-visual-cpp-overview.md)<br/>
有关如何存储和使用属性和目标的信息。

[用于生成命令和属性的常用宏](common-macros-for-build-commands-and-properties.md)<br/>
介绍可用于定义属性，例如路径和产品版本的宏 （编译时常量）。

[文件类型为创建C++项目](file-types-created-for-visual-cpp-projects.md)<br/>
描述各种类型的 Visual Studio 会创建不同的项目类型的文件。

[Visual StudioC++项目模板](visual-cpp-project-types.md)<br>
介绍可用于在基于 MSBuild 的项目类型C++。

[C++ 新项模板](using-visual-cpp-add-new-item-templates.md)<br>
介绍源文件和其他项可以添加到 Visual Studio 项目。

[预编译标头文件](../creating-precompiled-header-files.md)如何使用预编译标头文件以及如何创建自己的自定义预编译代码，以加快构建时间。

[Visual Studio 项目属性引用](property-pages-visual-cpp.md)<br/>
在 Visual Studio IDE 中设置的项目属性的参考文档。

## <a name="see-also"></a>请参阅

[C/C++ 生成参考](c-cpp-building-reference.md)