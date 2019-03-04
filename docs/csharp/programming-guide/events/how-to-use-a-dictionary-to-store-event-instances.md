---
title: HOW TO：使用字典儲存事件執行個體 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f3b8e313bd0b1bd3973102caebb9bbc9da620ae6
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203028"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="3e8f2-102">HOW TO：使用字典儲存事件執行個體 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3e8f2-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="3e8f2-103">`accessor-declarations` 的其中一個用途是公開許多事件，但不為每個事件配置欄位，而改為使用字典儲存事件執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e8f2-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="3e8f2-104">這只有在您有許多事件，但預期不會實作大多數事件時才有用。</span><span class="sxs-lookup"><span data-stu-id="3e8f2-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e8f2-105">範例</span><span class="sxs-lookup"><span data-stu-id="3e8f2-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="3e8f2-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e8f2-106">See also</span></span>

- [<span data-ttu-id="3e8f2-107">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3e8f2-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3e8f2-108">事件</span><span class="sxs-lookup"><span data-stu-id="3e8f2-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="3e8f2-109">委派</span><span class="sxs-lookup"><span data-stu-id="3e8f2-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
