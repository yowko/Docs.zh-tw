---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 19300a928a59c7259f81b282bd28d9bdd447d76b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872632"
---
# <a name="param-visual-basic"></a>\<param> (Visual Basic)

定義參數名稱和描述。  
  
## <a name="syntax"></a>語法  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>參數  

 `name`  
 方法參數的名稱。 以雙引號 (" ") 將名稱括起來。  
  
 `description`  
 參數的描述。  
  
## <a name="remarks"></a>備註  

 `<param>`標記應該用在方法宣告的批註中，以描述方法的其中一個參數。  
  
 標記的文字 `<param>` 將會出現在下列位置：  
  
- IntelliSense 的參數資訊。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。  
  
- 物件瀏覽器。 如需詳細資訊，請參閱 [查看程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 `<param>` 標記來描述 `id` 參數。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)
