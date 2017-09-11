---
title: "非同步伺服器程式設計 - C# 指南"
description: "了解使用非同步程式設計技術卸載伺服器工作負載的技巧"
keywords: "C#, 非同步, 受到 CPU 限制, 受到網路限制"
ms.date: 08/24/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7402b29b-1093-456d-be4c-f60ecb8926bb
redirect_url: /dotnet/csharp/tutorials/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 390d0eb2c8416165984ffe6c80ed6977e61a2845
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="-asynchronous-server-programming"></a><span data-ttu-id="70669-104">🔧非同步伺服器程式設計</span><span class="sxs-lookup"><span data-stu-id="70669-104">🔧 Asynchronous Server Programming</span></span>

> <span data-ttu-id="70669-105">**注意**</span><span class="sxs-lookup"><span data-stu-id="70669-105">**Note**</span></span>
> 
> <span data-ttu-id="70669-106">本主題尚未開稿！</span><span class="sxs-lookup"><span data-stu-id="70669-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="70669-107">歡迎您提供意見，協助擬定範圍和方向。</span><span class="sxs-lookup"><span data-stu-id="70669-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="70669-108">您可以追蹤狀態，並在 GitHub 提供關於此[問題](https://github.com/dotnet/docs/issues/952)的輸入。</span><span class="sxs-lookup"><span data-stu-id="70669-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/952) at GitHub.</span></span>
> 
> <span data-ttu-id="70669-109">如果您想要檢閱早期草稿和本主題的大綱，請在問題中留言並附上您的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="70669-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="70669-110">深入了解如何參與 [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)。</span><span class="sxs-lookup"><span data-stu-id="70669-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

