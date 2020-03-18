---
title: ASP.NET面向 WCF 開發人員的核心 gRPC - gRPC 面向 WCF 開發人員
description: 為 WCF 開發人員ASP.NET核心 3.0 構建 gRPC 服務簡介
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543231"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>適用於 WCF 開發人員的 ASP.NET Core gRPC

![封面影像](./media/cover.png)

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 by Microsoft Corporation

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書是以「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。

此處描述的一些範例僅供說明之用，純屬虛構。 並未影射或關聯任何真實的人、事、物。

Microsoft 與列於 https://www.microsoft.com「商標」網頁的商標是 Microsoft 集團的商標。

Docker 鯨魚標誌是 Docker， Inc. 經許可使用的注冊商標。

所有其他商標和標誌屬於其各自擁有者的財產。

作者：

> **馬克·倫德爾**- 首席技術官 -[視覺重碼](https://visualrecode.com)
>
> **米蘭達·施泰納**- 技術作者

編輯器：

> **Maira Wenzel** - Sr. 內容開發人員 - 微軟

## <a name="introduction"></a>簡介

gRPC 是構建網路服務和分散式應用程式的現代框架。 想像一下 Windows 通信基礎 （WCF） NetTCP 綁定的性能，以及 SOAP 的跨平臺互通性。 gRPC 基於 HTTP/2 和 Protobuf 消息編碼協議構建，以便在應用程式和服務之間提供高性能、低頻寬的通信。 它支援在最流行的程式設計語言和平臺上生成伺服器和用戶端代碼，包括 .NET、JAVA、Python、Node.js、Go 和C++。 ASP.NET Core 3.0 中對 gRPC 的一流支援，以及現有的 gRPC 工具和 .NET 4.x 的庫，對於希望在其組織中採用 .NET Core 的開發團隊而言，它是 WCF 的絕佳替代方案。

## <a name="who-should-use-this-guide"></a>誰應該使用本指南

本指南是為以前使用過 WCF 的 .NET 框架或 .NET Core 工作的開發人員編寫的，這些開發人員尋求將其應用程式遷移到用於 .NET Core 3.0 和更高版本的現代 RPC 環境。 更一般地說，如果要升級到 .NET Core 3.0，並且想要使用內置 gRPC 工具，本指南也很有用。

## <a name="how-you-can-use-this-guide"></a>此指南的使用方式

這是ASP.NET核心3.0中構建 gRPC 服務的簡短介紹，其中特別提到 WCF 作為類似平臺。 它解釋了 gRPC 的原則，將每個概念與 WCF 的等效功能相關聯，並為將現有的 WCF 應用程式遷移到 gRPC 提供了指導。 對於具有 WCF 經驗並希望學習 gRPC 以構建新服務的開發人員來說，它也很有用。 您可以將應用程式範例用作您自己的專案的範本或參考，並且可以自由地複製和重用書籍或其示例中的代碼。

請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。 讓每個人都從一組共同的術語和基本原則中工作，有助於確保架構模式和實踐的一致應用。

## <a name="references"></a>參考

- **gRPC 網站**
  <https://grpc.io>
- **在 .NET 核心和 .NET 框架之間選擇伺服器應用**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[下一步](introduction.md)
