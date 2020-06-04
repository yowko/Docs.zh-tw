---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 380923c2313450afc5745b25eeea6a444705dd3f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411521"
---
# <a name="see-visual-basic"></a>\<see> (Visual Basic)
指定另一個成員的連結。  
  
## <a name="syntax"></a>語法  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>參數  
 `member`  
 可從目前編譯環境呼叫的成員或欄位參考。 編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。 `member` 必須出現在雙引號內 (" ")。  
  
## <a name="remarks"></a>備註  
 使用 `<see>` 標記來指定文字內的連結。 使用 [\<seealso>](seealso.md) 表示您可能想要出現在「另請參閱」一節中的文字。  
  
 使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<see>` [備註] 區段中的標記 `UpdateRecord` 來參考 `DoesRecordExist` 方法。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)
