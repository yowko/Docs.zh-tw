---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 0a68cf0a495c2809961e8ec99effa459b0647fec
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866379"
---
# <a name="typeparam-visual-basic"></a>\<typeparam> (Visual Basic)

定義型別參數名稱和描述。  
  
## <a name="syntax"></a>語法  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>參數  

 `name`  
 型別參數的名稱。 以雙引號 (" ") 將名稱括起來。  
  
 `description`  
 類型參數的描述。  
  
## <a name="remarks"></a>備註  

 使用 `<typeparam>` 泛型型別或泛型成員宣告的批註中的標記，描述其中一個型別參數。  
  
 使用 [-doc](../../reference/command-line-compiler/doc.md) 進行編譯，以處理檔批註至檔案。  
  
## <a name="example"></a>範例  

 此範例會使用 `<typeparam>` 標記來描述 `id` 參數。  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)
