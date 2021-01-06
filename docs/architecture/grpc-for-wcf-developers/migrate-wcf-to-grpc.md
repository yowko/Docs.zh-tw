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
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="19188-103">將 WCF 解決方案移轉至 gRPC</span><span class="sxs-lookup"><span data-stu-id="19188-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="19188-104">本章將說明如何使用 ASP.NET Core 5.0 gRPC 專案，並示範如何將不同類型的 Windows Communication Foundation (WCF) 服務遷移至 gRPC 的對等專案：</span><span class="sxs-lookup"><span data-stu-id="19188-104">This chapter will describe how to work with ASP.NET Core 5.0 gRPC projects and demonstrate migrating different types of Windows Communication Foundation (WCF) services to the gRPC equivalent:</span></span>

- <span data-ttu-id="19188-105">建立 ASP.NET Core 5.0 gRPC 專案。</span><span class="sxs-lookup"><span data-stu-id="19188-105">Create an ASP.NET Core 5.0 gRPC project.</span></span>
- <span data-ttu-id="19188-106">GRPC 一元 RPC 的簡單要求-回復作業。</span><span class="sxs-lookup"><span data-stu-id="19188-106">Simple request-reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="19188-107">GRPC 用戶端串流 RPC 的單向作業。</span><span class="sxs-lookup"><span data-stu-id="19188-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="19188-108">GRPC 雙向串流 RPC 的全雙工服務。</span><span class="sxs-lookup"><span data-stu-id="19188-108">Full-duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="19188-109">此外，使用串流服務與重複欄位來傳回資料集的比較，以及本章結尾的使用用戶端程式庫的討論。</span><span class="sxs-lookup"><span data-stu-id="19188-109">There's also a comparison of using streaming services versus repeated fields for returning datasets, and there's a discussion of the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="19188-110">範例 WCF 應用程式是一組股票交易服務的最短存根。</span><span class="sxs-lookup"><span data-stu-id="19188-110">The sample WCF application is a minimal stub of a set of stock trading services.</span></span> <span data-ttu-id="19188-111">它會針對相依性插入，使用開放原始碼的控制反轉 (IoC) 容器庫（稱為 Autofac）。</span><span class="sxs-lookup"><span data-stu-id="19188-111">It uses the open-source Inversion of Control (IoC) container library called Autofac for dependency injection.</span></span> <span data-ttu-id="19188-112">它包含三個服務，每個 WCF 服務類型各一個。</span><span class="sxs-lookup"><span data-stu-id="19188-112">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="19188-113">這些服務將在下列各節中更詳細地討論。</span><span class="sxs-lookup"><span data-stu-id="19188-113">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="19188-114">您可以從 [dotnet-架構/grpc （適用](https://github.com/dotnet-architecture/grpc-for-wcf-developers) 于 GitHub 上的 wcf 開發人員）下載方案。</span><span class="sxs-lookup"><span data-stu-id="19188-114">You can download the solutions from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="19188-115">這些服務會使用假的資料來將外部相依性降至最低。</span><span class="sxs-lookup"><span data-stu-id="19188-115">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="19188-116">這些範例包含每個服務的 WCF 和 gRPC 執行。</span><span class="sxs-lookup"><span data-stu-id="19188-116">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="19188-117">[上一個](ws-protocols.md) 
>[下一步](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="19188-117">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
