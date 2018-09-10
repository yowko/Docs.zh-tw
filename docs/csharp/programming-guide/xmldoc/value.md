---
title: '&lt;value&gt; (C# 程式設計手冊)'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 24ef4aba13668cd04e20f17ebffac9eb68e796ca
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081852"
---
# <a name="ltvaluegt-c-programming-guide"></a>&lt;value&gt; (C# 程式設計手冊)
## <a name="syntax"></a>語法  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>參數  
 `property-description`  
 屬性的描述。  
  
## <a name="remarks"></a>備註  
 \<value> 標記可讓您描述屬性所代表的值。 請注意，當您在 Visual Studio .NET 開發環境中透過程式碼精靈新增屬性時，會新增新屬性的 [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) 標記。 您接著應該手動新增 \<value> 標記，來描述屬性所代表的值。  
  
 編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
