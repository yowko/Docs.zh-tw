---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 2ad54845645172acb5b91935f5347a828510e3aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411482"
---
# <a name="typeparam-visual-basic"></a>\<typeparam> (Visual Basic)
定義類型參數名稱和描述。  
  
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
 在 `<typeparam>` 泛型型別或泛型成員宣告的批註中使用標記，以描述其中一個類型參數。  
  
 使用[-doc](../../reference/command-line-compiler/doc.md)進行編譯，以處理檔案的檔批註。  
  
## <a name="example"></a>範例  
 這個範例會使用 `<typeparam>` 標記來描述 `id` 參數。  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>另請參閱

- [XML 註解標籤](index.md)
