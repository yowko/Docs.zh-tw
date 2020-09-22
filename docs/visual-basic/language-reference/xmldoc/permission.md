---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: ae6167f3582fe22cd10d9ef7a10873d6d9bdfa06
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872554"
---
# <a name="permission-visual-basic"></a>\<permission> (Visual Basic)

指定成員的必要許可權。  
  
## <a name="syntax"></a>語法  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>參數  

 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 轉譯為輸出 XML 中的標準項目名稱。 `member`以引號括住 ( "" ) 。  
  
 `description`  
 成員存取權的描述。  
  
## <a name="remarks"></a>備註  

 使用 `<permission>` 標記來記錄成員的存取。 使用 <xref:System.Security.PermissionSet> 類別來指定成員的存取權。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 這個範例會使用 `<permission>` 標記來描述 <xref:System.Security.Permissions.FileIOPermission> 方法所需的 `ReadFile` 。  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)
