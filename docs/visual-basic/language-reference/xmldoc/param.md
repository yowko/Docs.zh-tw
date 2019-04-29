---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4bcfe96361de9e196cb684ac4ba734f82442e25c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940890"
---
# <a name="param-visual-basic"></a>\<param > (Visual Basic)
定義的參數名稱和描述。  
  
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
 `<param>`標記應該在方法宣告的註解中用來描述其中一個方法的參數。  
  
 文字`<param>`標籤將會出現在下列位置：  
  
- IntelliSense 的 參數資訊。 如需詳細資訊，請參閱[使用 IntelliSense](/visualstudio/ide/using-intellisense)。  
  
- 物件瀏覽器。 如需詳細資訊，請參閱[檢視程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<param>`標記來描述`id`參數。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
