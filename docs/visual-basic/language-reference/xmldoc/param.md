---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4405fdf2defbb27aa2146d20083fd406d1f07236
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352291"
---
# <a name="param-visual-basic"></a>\<param > （Visual Basic）
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
 `<param>` 標記應該用於方法宣告的批註中，以描述方法的其中一個參數。  
  
 `<param>` 標記的文字會出現在下列位置：  
  
- IntelliSense 的參數資訊。 如需詳細資訊，請參閱 [Using IntelliSense](/visualstudio/ide/using-intellisense)。  
  
- 物件瀏覽器。 如需詳細資訊，請參閱[檢視程式碼的結構](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<param>` 標記來描述 `id` 參數。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
