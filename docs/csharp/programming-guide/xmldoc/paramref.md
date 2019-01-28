---
title: '&lt;paramref&gt; - C# 程式設計指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 21f8eb293a006a748c876a3b816eae3a799d3d7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640884"
---
# <a name="ltparamrefgt-c-programming-guide"></a>&lt;paramref&gt; (C# 程式設計手冊)
## <a name="syntax"></a>語法  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 要參考的參數名稱。 以雙引號 (" ") 括住名稱。  
  
## <a name="remarks"></a>備註  
 \<paramref> 標記提供一種方法來表示在程式碼註解中的字組，例如 \<summary> 或 \<remarks> 區塊中的字組指的是參數。 若要以某種不同方式 (例如，粗體或斜體字型) 格式化這個字組，您可以處理 XML 檔案。  
  
 編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
