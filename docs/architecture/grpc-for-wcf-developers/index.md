---
title: WCF 開發人員的 ASP.NET Core gRPC-WCF 開發人員的 gRPC
description: 在 WCF 開發人員的 ASP.NET Core 3.0 中建立 gRPC 服務的簡介
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b89f5974dd18e7005c6479c5b9eead039364e654
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738080"
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

此處所描述的一些範例僅供說明，純屬虛構。 任何實際關聯或連結純屬巧合。

Microsoft 與列於 https://www.microsoft.com 「商標」網頁的商標是 Microsoft 集團的商標。

Docker whale 標誌是 Docker，Inc. 的注冊商標，由許可權使用。

所有其他商標和標誌屬於其各自擁有者的財產。

作者:

> **Mark Rendle** -首席技術長-[視覺的編碼](https://visualrecode.com)
>
> **Miranda Steiner** -技術作者

編輯者：

> **Maira Wenzel** -Sr 內容開發人員-Microsoft

## <a name="introduction"></a>簡介

gRPC 是一種現代化的架構，可用於建立網路服務和分散式應用程式。 想像一下 WCF 的 NetTCP 系結與 SOAP 的跨平臺互通性的效能。 gRPC 是以 HTTP/2 和 Protobuf 訊息編碼通訊協定為基礎，可在應用程式與服務之間提供高效能、低頻寬的通訊。 它支援跨最受歡迎的程式設計語言和平臺（包括 .NET、JAVA、Python、node.js、Go 等等） C++產生伺服器和用戶端程式代碼。 有了 ASP.NET Core 3.0 中 gRPC 的第一級支援，除了適用于 .NET 4.x 的現有 gRPC 工具和程式庫之外，我們也認為它是 WCF 的絕佳替代方案，適用于想要在組織中採用 .NET Core 的開發團隊。

## <a name="who-should-use-this-guide"></a>誰應該使用本指南

本指南是針對在先前已使用 WCF 的 .NET Framework 或 .NET Core 中工作的開發人員所撰寫，而且想要將其應用程式遷移至 .NET Core 3.0 和更新版本的新式 RPC 環境。 本指南也可能更普遍用於升級或考慮升級至想要使用內建 gRPC 工具的 .NET Core 3.0 的開發人員。

## <a name="how-you-can-use-this-guide"></a>此指南的使用方式

這是在 ASP.NET Core 3.0 中建立 gRPC 服務的簡要介紹，並特別參考 WCF 做為類似的平臺。 其中說明 gRPC 的原則，並將每個概念關聯至 WCF 的對等功能，並提供將現有 WCF 應用程式遷移至 gRPC 的指引。 對於有 WCF 經驗，而且想要學習 gRPC 以建立新服務的開發人員而言，這也很有用。 範例應用程式可用來作為您自己專案的範本或參考，而且您可以免費複製並重複使用本書或其範例中的程式碼。

請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。 讓所有人都使用一組共用術語和基礎原則，有助確保套用一致的架構模式和做法。

## <a name="references"></a>reference

- **gRPC 網站**  
  <https://grpc.io>
- **針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[下一步](introduction.md)
