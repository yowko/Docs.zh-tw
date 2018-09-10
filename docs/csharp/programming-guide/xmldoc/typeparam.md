---
title: '&lt;typeparam&gt; (C# 程式設計手冊)'
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: ec19060008c1c06c54c89dbddee7d24001bcdebc
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273709"
---
# <a name="lttypeparamgt-c-programming-guide"></a>&lt;typeparam&gt; (C# 程式設計手冊)
## <a name="syntax"></a>語法  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a>參數  
 `name`  
 型別參數的名稱。 以雙引號 (" ") 括住名稱。  
  
 `description`  
 型別參數的描述。  
  
## <a name="remarks"></a>備註  
 `<typeparam>` 標記應該用於泛型型別或方法宣告的註解中，以描述型別參數。 新增泛型型別或方法之每個型別參數的標記。  
  
 如需詳細資訊，請參閱[泛型](../../../csharp/programming-guide/generics/index.md)。  
  
 `<typeparam>` 標記的文字將會顯示於 IntelliSense，即 [Object Browser Window](https://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) (物件瀏覽器視窗) 程式碼註解 Web 報告。  
  
 編譯搭配 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
