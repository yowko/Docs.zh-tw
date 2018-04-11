---
title: 非同步總覽
description: 了解非同步程式設計此一重要技術，如何讓您更容易處理對多個核心的封鎖 I/O 和並行作業。
keywords: .NET, .NET Core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f2dddc21dfb124fe97c397a156743981a67e4037
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="async-overview"></a><span data-ttu-id="20cd7-104">非同步總覽</span><span class="sxs-lookup"><span data-stu-id="20cd7-104">Async Overview</span></span>

<span data-ttu-id="20cd7-105">不久之前，只要購買較新的電腦或伺服器，應用程式的執行速度就會更快，然後逐漸停止。</span><span class="sxs-lookup"><span data-stu-id="20cd7-105">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="20cd7-106">這事實上相反。</span><span class="sxs-lookup"><span data-stu-id="20cd7-106">In fact, it reversed.</span></span> <span data-ttu-id="20cd7-107">具有 1ghz 單一核心 ARM 晶片和伺服器工作負載的行動電話已轉換為 VM。</span><span class="sxs-lookup"><span data-stu-id="20cd7-107">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="20cd7-108">使用者仍然想要回應式 UI，而且企業擁有者想要擁有隨其業務調整的伺服器。</span><span class="sxs-lookup"><span data-stu-id="20cd7-108">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="20cd7-109">行動和雲端以及已連接網際網路母體 >3B 使用者的轉換已導致新的一組軟體模式。</span><span class="sxs-lookup"><span data-stu-id="20cd7-109">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="20cd7-110">用戶端應用程式應該一律啟動、一律連線，並持續回應使用者互動 (例如觸控)，而且在應用程式市集具有高評價！</span><span class="sxs-lookup"><span data-stu-id="20cd7-110">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="20cd7-111">服務應該透過正常相應增加和相應減少來處理流量暴增情況。</span><span class="sxs-lookup"><span data-stu-id="20cd7-111">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="20cd7-112">非同步程式設計是一項重要技術，可讓您更容易處理對多個核心的封鎖 I/O 和並行作業。</span><span class="sxs-lookup"><span data-stu-id="20cd7-112">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="20cd7-113">.NET 提供使用 C#、VB 和 F# 的易用語言層級非同步程式設計模型，讓應用程式和服務具備回應性與彈性的功能。</span><span class="sxs-lookup"><span data-stu-id="20cd7-113">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="20cd7-114">為什麼撰寫非同步程式碼？</span><span class="sxs-lookup"><span data-stu-id="20cd7-114">Why Write Async Code?</span></span>

<span data-ttu-id="20cd7-115">現代應用程式大量使用檔案和網路 I/O。</span><span class="sxs-lookup"><span data-stu-id="20cd7-115">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="20cd7-116">除非您想要學習和使用具挑戰性的模式，否則 I/O API 傳統上預設會進行封鎖，進而導致不佳的使用者經驗和硬體使用。</span><span class="sxs-lookup"><span data-stu-id="20cd7-116">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="20cd7-117">工作架構非同步 API 和語言層級非同步程式設計模型則與此模型相反，只要學習幾個新的概念就可讓非同步執行成為預設值。</span><span class="sxs-lookup"><span data-stu-id="20cd7-117">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="20cd7-118">非同步程式碼具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="20cd7-118">Async code has the following characteristics:</span></span>

* <span data-ttu-id="20cd7-119">處理更多的伺服器要求，方法是在等候傳回 I/O 要求時產生執行緒以處理更多的要求。</span><span class="sxs-lookup"><span data-stu-id="20cd7-119">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="20cd7-120">讓 UI 更具回應性，方法是在等候 I/O 要求時產生 UI 互動的執行緒，以及將長時間執行的工作轉換成其他 CPU 核心。</span><span class="sxs-lookup"><span data-stu-id="20cd7-120">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="20cd7-121">許多較新的 .NET API 都是非同步的。</span><span class="sxs-lookup"><span data-stu-id="20cd7-121">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="20cd7-122">輕鬆地在 .NET 中撰寫非同步程式碼！</span><span class="sxs-lookup"><span data-stu-id="20cd7-122">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="20cd7-123">後續步驟</span><span class="sxs-lookup"><span data-stu-id="20cd7-123">What's next?</span></span>

<span data-ttu-id="20cd7-124">若要深入探討非同步概念和程式設計，請參閱[深入了解非同步](async-in-depth.md)和[工作架構非同步程式設計](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="20cd7-124">For a deep dive into async concepts and programming, see [Async in depth](async-in-depth.md) and [Task-based asynchronous programming](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span></span>
