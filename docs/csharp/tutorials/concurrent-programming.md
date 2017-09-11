---
title: "並行程式設計 - C# 指南"
description: "了解平行執行 (可能會受到 CPU 的限制) 工作的技術"
keywords: "C#, 非同步, 受到 CPU 限制, 受到網路限制"
ms.date: 08/24/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0f8b42de-858a-44a3-87d9-998211f26377
redirect_url: /dotnet/csharp/tutorials/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 00cf3b04178ca48c9f8f35eb16bc216389e6b272
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="-concurrent-programming"></a><span data-ttu-id="1f9fb-104">🔧 並行程式設計</span><span class="sxs-lookup"><span data-stu-id="1f9fb-104">🔧 Concurrent Programming</span></span>

> <span data-ttu-id="1f9fb-105">**注意**</span><span class="sxs-lookup"><span data-stu-id="1f9fb-105">**Note**</span></span>
> 
> <span data-ttu-id="1f9fb-106">本主題尚未開稿！</span><span class="sxs-lookup"><span data-stu-id="1f9fb-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="1f9fb-107">歡迎您提供意見，協助擬定範圍和方向。</span><span class="sxs-lookup"><span data-stu-id="1f9fb-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="1f9fb-108">您可以追蹤狀態，並在 GitHub 提供關於此[問題](https://github.com/dotnet/docs/issues/953)的輸入。</span><span class="sxs-lookup"><span data-stu-id="1f9fb-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/953) at GitHub.</span></span>
> 
> <span data-ttu-id="1f9fb-109">如果您想要檢閱早期草稿和本主題的大綱，請在問題中留言並附上您的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="1f9fb-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="1f9fb-110">深入了解如何參與 [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)。</span><span class="sxs-lookup"><span data-stu-id="1f9fb-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

