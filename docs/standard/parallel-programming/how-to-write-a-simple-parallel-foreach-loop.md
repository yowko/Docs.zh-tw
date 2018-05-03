---
title: 如何：撰寫簡單的 Parallel.ForEach 迴圈
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 90b900bf98ab664e0fce5c70573f01e044d70803
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>如何：撰寫簡單的 Parallel.ForEach 迴圈
此範例示範如何使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 迴圈來透過 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 資料來源啟用資料平行處理原則。  
  
> [!NOTE]
>  本文件使用 Lambda 運算式來定義 PLINQ 中的委派。 如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈的運作方式類似 <xref:System.Threading.Tasks.Parallel.For%2A> 迴圈。 來源集合會進行分割，並依據系統環境在多個執行緒上排定工作。 系統上的處理器愈多，平行方法的執行速度愈快。 對於某些來源集合，循序迴圈的執行速度可能更快，這取決於來源的大小和執行的工作種類。 如需效能的詳細資訊，請參閱[資料和工作平行處理原則中可能出現的錯誤](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 如需平行迴圈的詳細資訊，請參閱[如何： 撰寫簡單的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)。  
  
 若要將 <xref:System.Threading.Tasks.Parallel.ForEach%2A>使用於非泛型集合 ，可使用 <xref:System.Linq.Enumerable.Cast%2A> 擴充方法將集合轉換成泛型集合，如下列範例所示：  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 您也可以使用平行 LINQ (PLINQ) 來平行處理 <xref:System.Collections.Generic.IEnumerable%601> 資料來源。 PLINQ 可讓您使用宣告式查詢語法來表示迴圈行為。 如需詳細資訊，請參閱 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   複製此程式碼，並將其貼入 Visual Studio 2010 主控台應用程式專案。  
  
-   加入對 System.Net.Http 的參考  
  
-   按 F5 鍵  
  
## <a name="see-also"></a>請參閱  
 [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
