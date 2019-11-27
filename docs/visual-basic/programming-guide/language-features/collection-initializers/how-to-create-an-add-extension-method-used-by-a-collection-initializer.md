---
title: 如何：建立集合初始設定式所使用的 Add 擴充方法
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 6d5f9d38b413b79f111a14ec3829c57a9797ce54
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346717"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>如何：建立集合初始設定式所使用的 Add 擴充方法 (Visual Basic)
當您使用集合初始化運算式來建立集合時，Visual Basic 編譯器會搜尋集合類型的 `Add` 方法，其中 `Add` 方法的參數會符合集合初始化運算式中的數值型別。 這個 `Add` 方法是用來在集合中填入集合初始化運算式的值。  
  
 如果沒有相符的 `Add` 方法存在，而且您無法修改集合的程式碼，您可以加入名為 `Add` 的擴充方法，以接受集合初始化運算式所需的參數。 當您使用泛型集合的集合初始化運算式時，這通常是您需要執行的動作。  
  
## <a name="example"></a>範例  
 下列範例示範如何將擴充方法加入至泛型 <xref:System.Collections.Generic.List%601> 類型，以便將集合初始化運算式用來加入 `Employee`類型的物件。 擴充方法可讓您使用簡短的集合初始化運算式語法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>請參閱

- [集合初始設定式](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [如何：建立集合初始設定式所使用的集合](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
