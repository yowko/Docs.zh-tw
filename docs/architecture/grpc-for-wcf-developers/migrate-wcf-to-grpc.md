---
title: 將 wcf 方案遷移至 WCF 開發人員的 gRPC-gRPC
description: 如何將不同類型的 WCF 服務遷移至 gRPC 中的對等專案。
ms.date: 12/15/2020
ms.openlocfilehash: 3bd35cb6119368ff3db3be9ab5fabf89f2652b29
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97937957"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>將 WCF 解決方案移轉至 gRPC

本章將說明如何使用 ASP.NET Core 5.0 gRPC 專案，並示範如何將不同類型的 Windows Communication Foundation (WCF) 服務遷移至 gRPC 的對等專案：

- 建立 ASP.NET Core 5.0 gRPC 專案。
- GRPC 一元 RPC 的簡單要求-回復作業。
- GRPC 用戶端串流 RPC 的單向作業。
- GRPC 雙向串流 RPC 的全雙工服務。

此外，使用串流服務與重複欄位來傳回資料集的比較，以及本章結尾的使用用戶端程式庫的討論。

範例 WCF 應用程式是一組股票交易服務的最短存根。 它會針對相依性插入，使用開放原始碼的控制反轉 (IoC) 容器庫（稱為 Autofac）。 它包含三個服務，每個 WCF 服務類型各一個。 這些服務將在下列各節中更詳細地討論。 您可以從 [dotnet-架構/grpc （適用](https://github.com/dotnet-architecture/grpc-for-wcf-developers) 于 GitHub 上的 wcf 開發人員）下載方案。 這些服務會使用假的資料來將外部相依性降至最低。

這些範例包含每個服務的 WCF 和 gRPC 執行。

>[!div class="step-by-step"]
>[上一個](ws-protocols.md) 
>[下一步](create-project.md)
