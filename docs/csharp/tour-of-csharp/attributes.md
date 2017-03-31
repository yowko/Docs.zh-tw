---
title: "C# 屬性 | C# 語言教學課程"
description: "了解在 C 中使用屬性的宣告式程式設計#"
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5ef8b93bf0a2cf98c5251b888b61db9ab12d9a71
ms.lasthandoff: 03/13/2017

---

# <a name="attributes"></a>屬性

C# 程式中的型別、成員和其他實體支援控制其某方面行為的修飾詞。 例如，方法的協助工具是使用 `public`、`protected`、`internal` 和 `private` 修飾詞控制。 C# 將此能力一般化，宣告式資訊的使用者定義型別才能附加至程式實體，並在執行階段擷取。 程式是透過定義和使用***屬性***指定這項額外的宣告式資訊。

下列範例宣告的 `HelpAttribute` 屬性可置於程式實體，以提供其相關文件的連結。

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

所有屬性類別均衍生自標準程式庫提供的 @System.Attribute 基底類別。 在相關聯的宣告之前，於方括弧中提供屬性的名稱 (及任何引數) 即可套用屬性。 如果屬性名稱的結尾是 `Attribute`，則參考該屬性時可以省略該部分名稱。 例如，`HelpAttribute` 屬性可以下列方式使用。

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

這個範例會將 `HelpAttribute` 附加至 `Widget` 類別。 它會在類別的 `Display` 方法中加入另一個 `HelpAttribute`。 屬性類別的公用建構函式控制將屬性附加至程式實體時必須提供的資訊。 透過參考屬性類別的公用讀寫屬性可提供其他資訊 (例如先前對 `Topic` 的參考 )。

透過反射要求特定的屬性時，會以程式來源中提供的資訊叫用屬性類別的建構函式，並傳回產生的屬性執行個體。 如果是透過屬性提供其他資訊，傳回屬性執行個體之前，這些屬性會設為指定的值。

>[!div class="step-by-step"]
[上一步](delegates.md)

