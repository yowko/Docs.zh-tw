---
title: 以相鄰索引鍵將結果分組
description: 如何以相鄰索引鍵將結果分組。
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: a8d6ac133932a12154d5b23454065144c7652067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="group-results-by-contiguous-keys"></a>以相鄰索引鍵將結果分組

下例示範如何將項目分組到代表相鄰索引鍵子序列的區塊。 例如，假設您有以下序列的機碼值組︰  
  
|Key|值|  
|---------|-----------|  
|A|三|  
|A|think|  
|A|that|  
|B|Linq|  
|C|是|  
|A|really|  
|B|cool|  
|B|!|  
  
 會依此順序建立下列群組︰  
  
1.  We、think、that  
  
2.  Linq  
  
3.  is  
  
4.  really  
  
5.  cool、!  
  
 方案會實作為安全執行緒的擴充方法，並以資料流方式傳回其結果。 換句話說，它會在來源序列中移動時產生其群組。 不像 `group` 或 `orderby` 運算子，它可以在讀取所有序列之前，就開始將群組傳回給呼叫端。  
  
 在逐一查看來源序列時複製每個群組或區塊，可以達到執行緒安全，如原始程式碼註解中所述。 如果來源序列有大量的連續項目序列，Common Language Runtime 可能會擲回 <xref:System.OutOfMemoryException>。  
  
## <a name="example"></a>範例  
 下例範例會顯示擴充方法及使用它的用戶端程式碼。  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 若要在專案中使用擴充方法，請將 `MyExtensions` 靜態類別複製到新的或現有的來源程式碼檔案，如有需要，在命名空間所在新增其 `using` 指示詞。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ 查詢運算式](index.md)  
 
