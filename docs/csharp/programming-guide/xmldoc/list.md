---
title: '&lt;list&gt; - C# 程式設計指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: b960349d26a4addb5f4723bd7aa3f19b07e5f4d2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241544"
---
# <a name="ltlistgt-c-programming-guide"></a>&lt;list&gt; (C# 程式設計手冊)
## <a name="syntax"></a>語法  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
#### <a name="parameters"></a>參數  
 `term`  
 要定義的詞彙，可定義於 `description` 中。  
  
 `description`  
 項目符號或編號清單中的項目或者 `term` 的定義。  
  
## <a name="remarks"></a>備註  
 \<listheader> 區塊用來定義資料表或定義清單的標題資料列。 定義資料表時，您只需要提供標題中詞彙的項目。  
  
 清單中的每個項目都是使用 \<item> 區塊所指定。 建立定義清單時，您需要同時指定 `term` 和 `description`。 不過，針對資料表、項目符號清單或編號清單，您只需要提供 `description` 的項目。  
  
 清單或資料表可以有所需的多個 \<item> 區塊。  
  
 編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
