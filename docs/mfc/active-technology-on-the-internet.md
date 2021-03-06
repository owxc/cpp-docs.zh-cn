---
title: Internet 上的 Active 技术
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], Active technology
ms.assetid: 6f782aa1-5c2f-47a2-9e63-ddd0829d5a08
ms.openlocfilehash: e9f09715f53247cc8a3abf0fbc63517e76d810c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394918"
---
# <a name="active-technology-on-the-internet"></a>Internet 上的 Active 技术

Active 技术是一个开放式平台，用来让开发人员为全球性的 Internet 或公司的内部网络（也称为 Intranet）创建激动人心的动态内容和应用程序。 Microsoft 提供的用于 Internet 编程的主要技术如下所述。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

## <a name="activex-controls"></a>ActiveX 控件

ActiveX 控件（以前称为 OLE 控件）是一个对象，可插入网页或插入作为 ActiveX 控件容器的任何其他应用程序。 示例包括按钮、股票代码和图表控件。 有关详细信息，请参阅[Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)。

## <a name="internet-data-download-services"></a>Internet 数据下载服务

可以通过 Internet 使用以下普通协议下载数据：HTTP、 FTP 和 gopher。 MFC WinInet 类通过将 TCP/IP 和 WinSock 协议抽象化，使得可以很轻松地使用 HTTP、FTP 和 Gopher 协议传输数据。 MFC 异步名字对象类提供了一个方法，让您可以不受阻碍地下载文件和异步呈现大型对象。 有关详细信息，请参阅[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)。

## <a name="active-scripts"></a>活动脚本

VBScript 和其他脚本语言可连接控件和将交互式功能添加到网页。 脚本会将处理从服务器移动到客户端。 例如，可在客户端上验证窗体项然后将其发送到服务器。

## <a name="html-extensions"></a>HTML 扩展

HTML 扩展名（如对象标记）已添加以支持控件和脚本。

## <a name="see-also"></a>请参阅

[MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)<br/>
[Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)<br/>
[Win32 Internet 扩展 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
