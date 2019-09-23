---
title: WCF 開發人員的 ASP.NET Core gRPC-WCF 開發人員的 gRPC
description: 要寫入的
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7d02d7914aed39613b4a41da55515df80abddfe8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184446"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>WCF 開發人員的 ASP.NET Core gRPC

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

Docker 鯨魚標誌是 Docker, Inc. 的註冊商標。使用需要許可。

所有其他商標和標誌屬於其各自擁有者的財產。

作者:

> **Mark Rendle** -首席技術長-[視覺的編碼](https://visualrecode.com)
>
> **Miranda Steiner** -技術作者

編輯者：

> **Maira Wenzel** -Sr 內容開發人員-Microsoft

## <a name="introduction"></a>簡介

TODO

## <a name="purpose"></a>用途

TODO

## <a name="who-should-use-this-guide"></a>誰應該使用本指南

**更新此**

本指南的物件是 WCF 開發人員、開發組長和架構設計人員，有興趣將 .NET 4 和更早版本的 WCF 方案遷移到使用 gRPC services ASP.NET Core 3.0。

## <a name="how-you-can-use-this-guide"></a>此指南的使用方式

**更新此**

這是在 ASP.NET Core 3.0 中建立 gRPC 服務的簡要介紹，並特別參考 WCF 做為類似的平臺。 其中說明 gRPC 的原則，並將每個概念關聯至 WCF 的對等功能，並提供將現有 WCF 應用程式遷移至 gRPC 的指引。 對於有 WCF 經驗，而且想要學習 gRPC 以建立新服務的開發人員而言，這也很有用。 範例應用程式可用來作為您自己專案的範本或參考，而且您可以免費複製並重複使用本書或其範例中的程式碼。

請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。 讓所有人都使用一組共用術語和基礎原則，有助確保套用一致的架構模式和做法。

## <a name="references"></a>reference

- **gRPC 網站**  
  <https://grpc.io>
- **針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[下一步](introduction.md)
