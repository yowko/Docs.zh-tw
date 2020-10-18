---
title: 使用屬性擴充中繼資料
description: 瞭解如何在 .NET 中使用屬性擴充中繼資料。 屬性是類似關鍵字的描述性宣告，可標注程式設計項目，例如類型和欄位。
ms.date: 10/14/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- metadata, extending
- attributes [.NET], metadata
- elements [.NET], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
ms.openlocfilehash: 5678e904afae4d348fbb56b189c95cd59b8e7a4d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162839"
---
# <a name="extend-metadata-using-attributes"></a>使用屬性擴充中繼資料

Common Language Runtime 可讓您加入稱為屬性 (Attribute) 之類似關鍵字的描述性宣告，以標註類型、欄位、方法和屬性 (Property) 等程式設計項目。 當您編譯執行階段的程式碼時，它會轉換成 Microsoft 中繼語言 (MSIL)，並與編譯器所產生的中繼資料一起放在可攜式執行檔 (PE) 中。 屬性可讓您將額外的描述性資訊放入中繼資料，其可使用執行階段反映服務來擷取。 編譯器會在您宣告衍生自 <xref:System.Attribute?displayProperty=nameWithType> 的特殊類別執行個體時建立屬性。

.NET 會基於各種原因而使用屬性，並解決一些問題。 屬性描述如何序列化資料、指定用來強制執行安全性的特性，以及限制 Just-in-Time (JIT) 編譯器的最佳化程度，讓程式碼保持易於偵錯。 屬性也可記錄檔案名稱或程式碼作者，或者在表單開發期間控制控制項和成員的可見性。

## <a name="related-articles"></a>相關文章

|標題|描述|
|-----------|-----------------|
|[套用屬性](applying-attributes.md)|描述如何將屬性套用至您程式碼的項目。|
|[撰寫自訂屬性](writing-custom-attributes.md)|描述如何設計自訂屬性類別。|
|[擷取儲存於屬性中的資訊](retrieving-information-stored-in-attributes.md)|描述如何針對載入執行內容中的程式碼擷取自訂屬性。|
|[中繼資料和 Self-Describing 元件](../metadata-and-self-describing-components.md)|提供中繼資料的概觀，並描述如何在 .NET Framework 可攜式執行檔 (PE) 中實作。|
|[如何：將組件載入僅限反映的內容](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|說明如何擷取僅限反映的內容中的自訂屬性資訊。|

## <a name="reference"></a>參考

- <xref:System.Attribute?displayProperty=nameWithType>
