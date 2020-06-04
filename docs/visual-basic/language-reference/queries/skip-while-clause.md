---
title: Skip While 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: b357320a92ace1b7a261991737ed653d54d0eeab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359641"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While 子句 (Visual Basic)
只要指定的條件為 `true`，即略過集合中的項目，然後傳回其餘項目。  
  
## <a name="syntax"></a>語法  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`expression`|必要。 運算式，表示要測試元素的條件。 運算式必須傳回 `Boolean` 值或功能對等用法，例如 `Integer` 要評估為的 `Boolean` 。|  
  
## <a name="remarks"></a>備註  
 `Skip While`子句會略過查詢結果開頭的元素，直到提供的傳回 `expression` 為止 `false` 。 傳回 `expression` 之後 `false` ，查詢會傳回所有剩餘的元素。 `expression`會忽略其餘結果的。  
  
 `Skip While`子句與子句不同之處在于 `Where` ， `Where` 子句可以用來排除不符合特定條件之查詢中的所有元素。 `Skip While`子句只會排除元素，直到第一次不符合條件為止。 `Skip While`當您使用已排序的查詢結果時，子句最有用。  
  
 您可以使用子句，從查詢結果的開頭略過特定數目的結果 `Skip` 。  
  
## <a name="example"></a>範例  
 下列程式碼範例會使用 `Skip While` 子句來略過結果，直到找到美國的第一個客戶為止。  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [查詢](index.md)
- [Select 子句](select-clause.md)
- [From 子句](from-clause.md)
- [Skip 子句](skip-clause.md)
- [Take While 子句](take-while-clause.md)
- [Where 子句](where-clause.md)
