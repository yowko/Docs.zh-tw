---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: d7aacc5faea22f9c5a4b865a32c832154fe624c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872615"
---
# <a name="paramref-visual-basic"></a>\<paramref> (Visual Basic)

將單字格式化為參數。  
  
## <a name="syntax"></a>語法  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a>參數  

 `name`  
 要參考的參數名稱。 以雙引號 (" ") 將名稱括起來。  
  
## <a name="remarks"></a>備註  

 `<paramref>`標記可讓您表示單字是參數。 您可以處理 XML 檔案，以某種不同的方式格式化此參數。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 `<paramref>` 標記來參考 `id` 參數。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)
