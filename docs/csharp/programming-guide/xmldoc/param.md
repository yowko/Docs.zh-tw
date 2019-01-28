---
title: '&lt;param&gt; - C# 程式設計指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: fb31e1d4c39888765fe3e55674d5b6d18b9d5b65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641014"
---
# <a name="ltparamgt-c-programming-guide"></a>&lt;param&gt; (C# 程式設計手冊)
## <a name="syntax"></a>語法  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 方法參數的名稱。 以雙引號 (" ") 將名稱括起來。  
  
 `description`  
 參數的描述。  
  
## <a name="remarks"></a>備註  
 \<param> 標記應該在方法宣告的註解中用來描述參數的其中一個方法。 若要記錄多個參數，請使用多個 \<param > 標記。  
  
 \<param> 標記的文字將會顯示於 IntelliSense (即物件瀏覽器) 以及程式碼結構 Web 報告中。  
  
 編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
