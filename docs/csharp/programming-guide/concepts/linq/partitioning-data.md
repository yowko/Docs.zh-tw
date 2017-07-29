---
title: "分割資料 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2f1690dac93d5e74f1305bd457f8bc749bec5449
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="partitioning-data-c"></a>分割資料 (C#)
LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。  
  
 下圖顯示字元序列三種不同分割作業的結果。 第一項作業會傳回序列中的前三個項目。 第二項作業會略過前三個項目，傳回其餘項目。 第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。  
  
 ![LINQ 分割作業](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 分割序列的標準查詢運算子方法詳列於下一節。  
  
## <a name="operators"></a>運算子  
  
|運算子名稱|描述|C# 查詢運算式語法|更多資訊|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|略過項目直至序列中指定的位置為止。|不適用。|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|SkipWhile|根據述詞函式跳過項目，直到不符合條件的項目為止。|不適用。|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|Take|採用序列中最多到指定位置為止的項目。|不適用。|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|TakeWhile|根據述詞函式採用項目，直到不符合條件的項目為止。|不適用。|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>   
 [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

