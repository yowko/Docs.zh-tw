---
title: 如何：建立集合初始設定式所使用的 Add 擴充方法
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: c36fab6635a9f7820c52c5f73c20487b92879b9a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086344"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>如何：建立集合初始設定式所使用的 Add 擴充方法 (Visual Basic)

當您使用集合初始化運算式建立集合時，Visual Basic 編譯器會搜尋 `Add` 集合型別的方法，而該方法的參數與 `Add` 集合初始化運算式中的數值型別相符。 這個 `Add` 方法是用來在集合中填入集合初始化運算式中的值。  
  
 如果沒有相符的 `Add` 方法，且您無法修改集合的程式碼，您可以加入名為的擴充方法， `Add` 這個方法會採用集合初始化運算式所需的參數。 當您使用泛型集合的集合初始化運算式時，通常需要執行這項作業。  
  
## <a name="example"></a>範例  

 下列範例示範如何將擴充方法加入至泛型型別， <xref:System.Collections.Generic.List%601> 讓集合初始化運算式可以用來加入型別的物件 `Employee` 。 擴充方法可讓您使用縮短的集合初始化運算式語法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [集合初始化運算式](index.md)
- [如何：建立集合初始設定式所使用的集合](how-to-create-a-collection-used-by-a-collection-initializer.md)
