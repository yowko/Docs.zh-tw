---
title: '&lt;權限&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: bcec5d968f5d0c5400c28e772df151b164888a47
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539521"
---
# <a name="ltpermissiongt-visual-basic"></a>&lt;權限&gt;(Visual Basic)
指定必要的權限的成員。  
  
## <a name="syntax"></a>語法  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。 括住`member`引號 ("")。  
  
 `description`  
 成員存取權的描述。  
  
## <a name="remarks"></a>備註  
 使用`<permission>`標記來記載成員存取權。 使用<xref:System.Security.PermissionSet>類別，以指定成員的存取權。  
  
 編譯搭配 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用`<permission>`標記來描述所<xref:System.Security.Permissions.FileIOPermission>需要`ReadFile`方法。  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
