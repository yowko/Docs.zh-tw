---
title: <permission> （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 904d573514bf35b773d47321b7fd3b6a86e90262
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524696"
---
# <a name="permission-visual-basic"></a>\<permission > （Visual Basic）
指定成員的必要許可權。  
  
## <a name="syntax"></a>語法  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。 將 `member` 括在引號（""）中。  
  
 `description`  
 成員存取權的描述。  
  
## <a name="remarks"></a>備註  
 使用 `<permission>` 標記來記錄成員的存取。 使用 <xref:System.Security.PermissionSet> 類別來指定成員的存取權。  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<permission>` 標記來描述 `ReadFile` 方法所需的 <xref:System.Security.Permissions.FileIOPermission>。  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
