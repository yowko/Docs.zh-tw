---
title: "建立巢狀群組"
description: "如何建立巢狀群組。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 361ac1f224c6eef292fcf8434c7e465c9448b19c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="create-a-nested-group"></a><span data-ttu-id="e2012-104">建立巢狀群組</span><span class="sxs-lookup"><span data-stu-id="e2012-104">Create a nested group</span></span>

<span data-ttu-id="e2012-105">下列範例示範如何在 LINQ 查詢運算式中建立巢狀群組。</span><span class="sxs-lookup"><span data-stu-id="e2012-105">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="e2012-106">每個根據學年或年級層級建立的群組，接著會根據每個人的姓名進一步細分為群組。</span><span class="sxs-lookup"><span data-stu-id="e2012-106">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2012-107">範例</span><span class="sxs-lookup"><span data-stu-id="e2012-107">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="e2012-108">這個範例包含[查詢物件的集合](query-a-collection-of-objects.md)中範例程式碼中定義的物件參考。</span><span class="sxs-lookup"><span data-stu-id="e2012-108">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 <span data-ttu-id="e2012-109">[!code-cs[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e2012-109">[!code-cs[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]</span></span>  
  
 <span data-ttu-id="e2012-110">請注意，需要有三個巢狀 `foreach` 迴圈，才能逐一查看巢狀群組的內部項目。</span><span class="sxs-lookup"><span data-stu-id="e2012-110">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2012-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2012-111">See also</span></span>  
 [<span data-ttu-id="e2012-112">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="e2012-112">LINQ Query Expressions</span></span>](index.md)

