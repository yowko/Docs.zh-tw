---
title: 如何：建立集合初始設定式所使用的 Add 擴充方法
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 4dbe6146b70181864a6717146071f9b93a1f583e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414565"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>如何：建立集合初始設定式所使用的 Add 擴充方法 (Visual Basic)
當您使用集合初始化運算式來建立集合時，Visual Basic 編譯器會搜尋 `Add` 集合類型的方法，其中方法的參數會 `Add` 符合集合初始化運算式中的數值型別。 這個 `Add` 方法是用來在集合中填入集合初始化運算式的值。  
  
 如果沒有相符 `Add` 的方法存在，而且您無法修改集合的程式碼，您可以加入名為的擴充方法，其 `Add` 會接受集合初始化運算式所需的參數。 當您使用泛型集合的集合初始化運算式時，這通常是您需要執行的動作。  
  
## <a name="example"></a>範例  
 下列範例示範如何將擴充方法加入至泛型 <xref:System.Collections.Generic.List%601> 類型，讓集合初始化運算式可以用來加入類型的物件 `Employee` 。 擴充方法可讓您使用簡短的集合初始化運算式語法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [集合初始化運算式](index.md)
- [如何：建立集合初始設定式所使用的集合](how-to-create-a-collection-used-by-a-collection-initializer.md)
