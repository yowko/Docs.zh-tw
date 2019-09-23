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
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="e12e4-103">將 WCF 方案遷移至 gRPC</span><span class="sxs-lookup"><span data-stu-id="e12e4-103">Migrate a WCF solution to gRPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e12e4-104">本章將探討如何使用 ASP.NET Core 3.0 gRPC 專案，並示範如何將不同類型的 WCF 服務遷移至 gRPC 對應項：</span><span class="sxs-lookup"><span data-stu-id="e12e4-104">This chapter will look at how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of WCF service to the gRPC equivalent:</span></span>

- <span data-ttu-id="e12e4-105">建立 ASP.NET Core 3.0 gRPC 專案。</span><span class="sxs-lookup"><span data-stu-id="e12e4-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="e12e4-106">簡單的要求-回復作業，以 gRPC 一元 RPC。</span><span class="sxs-lookup"><span data-stu-id="e12e4-106">Simple Request-Reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="e12e4-107">GRPC 用戶端串流 RPC 的單向作業。</span><span class="sxs-lookup"><span data-stu-id="e12e4-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="e12e4-108">用來 gRPC 雙向串流 RPC 的全雙工服務。</span><span class="sxs-lookup"><span data-stu-id="e12e4-108">Full Duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="e12e4-109">此外，使用串流服務與重複的欄位來傳回資料集，以及在本章結尾處使用用戶端程式庫的比較。</span><span class="sxs-lookup"><span data-stu-id="e12e4-109">There's also a comparison of using streaming services versus repeated fields for returning data sets, and the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="e12e4-110">範例 WCF 應用程式是一組股票交易服務的最小 stub，使用稱為*Autofac*的開放原始碼的反轉控制（IoC）容器程式庫來進行相依性插入。</span><span class="sxs-lookup"><span data-stu-id="e12e4-110">The sample WCF application is a minimal stub of a set of stock trading services, using the open-source Inversion of Control (IoC) container library called *Autofac* for dependency injection.</span></span> <span data-ttu-id="e12e4-111">其中包含三個服務，每個 WCF 服務類型各一個。</span><span class="sxs-lookup"><span data-stu-id="e12e4-111">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="e12e4-112">下列各節將更詳細地討論這些服務。</span><span class="sxs-lookup"><span data-stu-id="e12e4-112">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="e12e4-113">您可以從 GitHub 上的[RendleLabs/grpc for wcf 開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers)下載解決方案。</span><span class="sxs-lookup"><span data-stu-id="e12e4-113">The solutions can be downloaded from [RendleLabs/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="e12e4-114">服務會使用假資料來將外部相依性降至最低。</span><span class="sxs-lookup"><span data-stu-id="e12e4-114">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="e12e4-115">這些範例包含每個服務的 WCF 和 gRPC 的執行。</span><span class="sxs-lookup"><span data-stu-id="e12e4-115">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e12e4-116">[上一頁](ws-protocols.md)
>[下一頁](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="e12e4-116">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
