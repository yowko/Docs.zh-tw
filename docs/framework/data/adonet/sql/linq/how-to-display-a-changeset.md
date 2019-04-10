---
title: HOW TO：顯示變更集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: 92acee0d36634ea09c245418fcc7a8b97d208aa6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228625"
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="8d5e8-102">HOW TO：顯示變更集</span><span class="sxs-lookup"><span data-stu-id="8d5e8-102">How to: Display a ChangeSet</span></span>
<span data-ttu-id="8d5e8-103">您可以使用 <xref:System.Data.Linq.DataContext> 來檢視 <xref:System.Data.Linq.DataContext.GetChangeSet%2A> 所追蹤的變更。</span><span class="sxs-lookup"><span data-stu-id="8d5e8-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d5e8-104">範例</span><span class="sxs-lookup"><span data-stu-id="8d5e8-104">Example</span></span>  
 <span data-ttu-id="8d5e8-105">下列範例會擷取所在城市是 London 的客戶、將城市變更為 Paris，並將變更送回給資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d5e8-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="8d5e8-106">這個程式碼的輸出會與下列類似。</span><span class="sxs-lookup"><span data-stu-id="8d5e8-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="8d5e8-107">請注意，結尾的摘要會顯示進行了八項變更。</span><span class="sxs-lookup"><span data-stu-id="8d5e8-107">Note that the summary at the end shows that eight changes were made.</span></span>  

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
  
## <a name="see-also"></a><span data-ttu-id="8d5e8-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d5e8-108">See also</span></span>

- [<span data-ttu-id="8d5e8-109">偵錯支援</span><span class="sxs-lookup"><span data-stu-id="8d5e8-109">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
