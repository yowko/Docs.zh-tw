---
title: 如何：在管線中使用封鎖集合的陣列
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: 2309676435a6603aaa9bbbd95953c0179b908622
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287827"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="dd0cd-102">如何：在管線中使用封鎖集合的陣列</span><span class="sxs-lookup"><span data-stu-id="dd0cd-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="dd0cd-103">下列範例示範如何搭配使用 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> 物件的陣列與靜態方法 (例如 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A>)，來實作元件之間的快速且彈性資料傳輸。</span><span class="sxs-lookup"><span data-stu-id="dd0cd-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd0cd-104">範例</span><span class="sxs-lookup"><span data-stu-id="dd0cd-104">Example</span></span>  
 <span data-ttu-id="dd0cd-105">下列範例示範基本管線實作，其中，每個物件都同時從輸入集合擷取資料，並轉換資料，然後將資料傳遞至輸出集合。</span><span class="sxs-lookup"><span data-stu-id="dd0cd-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="dd0cd-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd0cd-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="dd0cd-107">安全線程集合</span><span class="sxs-lookup"><span data-stu-id="dd0cd-107">Thread-Safe Collections</span></span>](index.md)
