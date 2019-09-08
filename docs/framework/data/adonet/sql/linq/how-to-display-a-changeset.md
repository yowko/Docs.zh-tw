---
title: 作法：顯示變更集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: 5f49e123e6e980501d330eeecf2719023cdff8e7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781973"
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="1204f-102">作法：顯示變更集</span><span class="sxs-lookup"><span data-stu-id="1204f-102">How to: Display a ChangeSet</span></span>
<span data-ttu-id="1204f-103">您可以使用 <xref:System.Data.Linq.DataContext> 來檢視 <xref:System.Data.Linq.DataContext.GetChangeSet%2A> 所追蹤的變更。</span><span class="sxs-lookup"><span data-stu-id="1204f-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1204f-104">範例</span><span class="sxs-lookup"><span data-stu-id="1204f-104">Example</span></span>  
 <span data-ttu-id="1204f-105">下列範例會擷取所在城市是 London 的客戶、將城市變更為 Paris，並將變更送回給資料庫。</span><span class="sxs-lookup"><span data-stu-id="1204f-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="1204f-106">這個程式碼的輸出會與下列類似。</span><span class="sxs-lookup"><span data-stu-id="1204f-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="1204f-107">請注意，結尾的摘要會顯示進行了八項變更。</span><span class="sxs-lookup"><span data-stu-id="1204f-107">Note that the summary at the end shows that eight changes were made.</span></span>  

 ```console
CustomerID: AROUT
   Original value: London
   Updated value: Paris
CustomerID: BSBEV
   Original value: London
   Updated value: Paris
CustomerID: CONSH
   Original value: London
   Updated value: Paris
CustomerID: EASTC
   Original value: London
   Updated value: Paris
CustomerID: NORTS
    Original value: London
    Updated value: Paris
CustomerID: PARIS
    Original value: London
    Updated value: Paris
CustomerID: SEVES
    Original value: London
    Updated value: Paris
CustomerID: SPECD
    Original value: London
    Updated value: Paris
Total changes: {Added: 0, Removed: 0, Modified: 8}
```
  
## <a name="see-also"></a><span data-ttu-id="1204f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1204f-108">See also</span></span>

- [<span data-ttu-id="1204f-109">偵錯支援</span><span class="sxs-lookup"><span data-stu-id="1204f-109">Debugging Support</span></span>](debugging-support.md)
