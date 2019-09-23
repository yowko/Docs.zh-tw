---
title: 將 WCF 方案遷移至 WCF 開發人員的 gRPC-gRPC
description: 如何將不同類型的 WCF 服務遷移至 gRPC 中的對等。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a9cfb87361194d998a3c4dfff4fe434be64f0d65
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184292"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>將 WCF 方案遷移至 gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

本章將探討如何使用 ASP.NET Core 3.0 gRPC 專案，並示範如何將不同類型的 WCF 服務遷移至 gRPC 對應項：

- 建立 ASP.NET Core 3.0 gRPC 專案。
- 簡單的要求-回復作業，以 gRPC 一元 RPC。
- GRPC 用戶端串流 RPC 的單向作業。
- 用來 gRPC 雙向串流 RPC 的全雙工服務。

此外，使用串流服務與重複的欄位來傳回資料集，以及在本章結尾處使用用戶端程式庫的比較。

範例 WCF 應用程式是一組股票交易服務的最小 stub，使用稱為*Autofac*的開放原始碼的反轉控制（IoC）容器程式庫來進行相依性插入。 其中包含三個服務，每個 WCF 服務類型各一個。 下列各節將更詳細地討論這些服務。 您可以從 GitHub 上的[RendleLabs/grpc for wcf 開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers)下載解決方案。 服務會使用假資料來將外部相依性降至最低。

這些範例包含每個服務的 WCF 和 gRPC 的執行。

>[!div class="step-by-step"]
>[上一頁](ws-protocols.md)
>[下一頁](create-project.md)
