---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 62f70ae7f40fa3cde9492563b7bd14dfa5940a5f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352235"
---
# <a name="returns-visual-basic"></a>\<會傳回 > （Visual Basic）
指定屬性或函數的傳回值。  
  
## <a name="syntax"></a>語法  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>參數  
 `description`  
 傳回值的描述。  
  
## <a name="remarks"></a>備註  
 在方法宣告的批註中使用 `<returns>` 標記，以描述傳回值。  
  
 使用 [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) 編譯可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<returns>` 標記來說明 `DoesRecordExist` 函數傳回的內容。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)
