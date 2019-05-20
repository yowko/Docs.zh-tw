---
title: namespace 關鍵字 - C# 參考
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: f938e49267faad8aebbf4c22fc921f305d160123
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633430"
---
# <a name="namespace-c-reference"></a>namespace (C# 參考)

`namespace` 關鍵字用來宣告包含一組相關物件的範圍。 您可以使用命名空間來組織程式碼項目，並建立全域唯一的型別。

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a>備註

在命名空間內，您可以宣告下列一或多個類型：

- 另一個命名空間

- [class](class.md)

- [interface](interface.md)

- [struct](struct.md)

- [enum](enum.md)

- [delegate](delegate.md)

無論是否在 C# 來源檔案中明確宣告命名空間，編譯器都會加入預設的命名空間。 這個未命名的命名空間，有時候是指全域命名空間，會出現在每個檔案中。 全域命名空間中的任何識別項都可用於具名命名空間中。

命名空間以隱含方式具有公用存取，且不可修改。 如需可在命名空間中指派給項目之存取修飾詞的討論，請參閱[存取修飾詞](access-modifiers.md)。

您可在兩個或多個宣告中定義命名空間。 例如，下例會將兩個類別定義為 `MyCompany` 命名空間的一部分︰

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a>範例

下例顯示如何在巢狀命名空間中呼叫靜態方法。

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a>相關資源

如需使用命名空間的詳細資訊，請參閱下列主題：

- [命名空間](../../programming-guide/namespaces/index.md)

- [使用命名空間](../../programming-guide/namespaces/using-namespaces.md)

- [如何：使用全域命名空間別名](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../../language-reference/index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [命名空間關鍵字](namespace-keywords.md)
- [using](using-directive.md)
- [使用靜態](using-static.md)
