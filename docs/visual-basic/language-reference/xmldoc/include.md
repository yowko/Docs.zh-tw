---
title: <include> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 8159613036942d6c79f50b59a9b24ede02b6e4d8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483584"
---
# <a name="include-visual-basic"></a>\<包含 > (Visual Basic)
參考描述的類型和成員在原始程式碼中的另一個檔案。  
  
## <a name="syntax"></a>語法  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>參數  
 `filename`  
 必要項。 包含文件的檔案名稱。 檔案名稱可以使用路徑進行限定。 括住`filename`以雙引號 ("")。  
  
 `tagpath`  
 必要項。 `filename` 中導致 `name` 標記的標記路徑。 請將路徑括在雙引號 ("")。  
  
 `name`  
 必要項。 在註解前面的標記名稱規範。 `Name` 將會有`id`。  
  
 `id`  
 必要項。 位在註解前面的標記識別碼。 請將識別碼括在單引號 (' ')。  
  
## <a name="remarks"></a>備註  
 使用`<include>`標記來參考另一個檔案中描述的類型的註解和在原始程式碼中的成員。 這是將文件註解直接放在原始程式碼檔中的替代方案。  
  
 `<include>`標記使用 W3C XML 路徑語言 (XPath) 1.0 版建議事項。 如需有關如何自訂您`<include>`使用，請參閱<https://www.w3.org/TR/xpath>。  
  
## <a name="example"></a>範例  
 這個範例會使用`<include>`從名為的檔案匯入成員文件註解的標記`commentFile.xml`。  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 格式`commentFile.xml`如下所示。  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>另請參閱
- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
