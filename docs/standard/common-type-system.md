---
title: 一般類型系統和 Common Language Specification
description: 了解一般型別系統 (CTS) 和 Common Language Specification (CLS) 如何讓 .NET 能夠支援多種語言。
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: 992f70cc7c2e55a0a2cfd08e08a3a9f16aad8c8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569544"
---
# <a name="common-type-system--common-language-specification"></a>一般類型系統和 Common Language Specification

同樣地，這是在 .NET 世界內自由使用的兩個詞彙，它們實際上對了解 .NET 實作如何啟用多語言開發和其運作方式十分重要。

## <a name="common-type-system"></a>一般類型系統

若要從頭開始，請記住，.NET 實作「無從驗證語言」。 這不只是表示程式設計人員可以使用任何可編譯為 IL 的語言來撰寫自己的程式碼。 也表示其必須能夠與使用其他語言所撰寫的程式碼互動，而這些語言可以在 .NET 實作上使用。

若要透明地執行這項操作，必須要有通用的方式來描述所有支援的類型。 這是一般類型系統 (CTS) 負責執行的作業。 它是用來執行下列事項︰

*   建立跨語言執行的架構。
*   提供物件導向模型，以支援在 .NET 實作上實作各種語言。
*   定義所有語言在需要處理類型時必須遵循的一組規則。
*   提供包含基礎基本型別 (例如 `Boolean`、`Byte`、`Char` 等) 的程式庫，以便用於應用程式開發。

CTS 定義應該支援的兩種主要類型︰參考和實值類型。 它們的名稱會指向其定義。

參考類型的物件是由物件實際值的參考來表示；這裡的參考類似 C/C++ 中的指標。 它指的就是物件值所在的記憶體位置。 這對這些類型的使用方式具有深遠影響。 如果您將參考類型指派給變數，然後將該變數傳遞給方法，例如，物件的任何變更都會反映在主要物件中；未進行複製。

如果物件是由物件的值來表示，則實值類型就是相反值。 如果您將實值類型指派給變數，則基本上會複製物件的值。

CTS 定義數種分類的類型，各有其特定語意和用法︰

*   類別
*   結構
*   列舉
*   介面
*   委派

CTS 也會定義類型的所有其他屬性 (例如存取修飾詞)、什麼是有效類型成員、繼承和多載的運作方式等。 不幸的是，深入探討其中任何項目不在簡介文章的範圍 (例如這項)，但您可以查閱涵蓋這些主題之更深入內容連結結尾的[更多資源](#more-resources)一節。

## <a name="common-language-specification"></a>Common Language Specification

若要啟用完整互通性案例，則透過程式碼建立的所有物件都必須依賴使用它們之語言的一些共通性 (即其_呼叫端_)。 因為有多種不同的語言，所以 .NET 已透過 **Common Language Specification** (CLS) 指定這些共通性。 CLS 定義許多常見應用程式所需的一組功能。 它也提供一種方法，以在需要支援的 .NET 上實作任何語言。

CLS 是 CTS 的子集。 除非 CLS 規則更嚴格，否則這表示 CTS 中的所有規則也適用於 CLS。 如果元件只是使用 CLS 中的規則所建置 (亦即，它只會在其 API 中公開 CLS 功能)，表示**符合 CLS 標準**。 例如，`<framework-librares>` 完全符合 CLS 標準，原因是它們需要作用於 .NET 上支援的所有語言。

您可以查閱下面[更多資源](#more-resources)一節中的文件，以取得 CLS 中所有功能的概觀。

## <a name="more-resources"></a>更多資源

*   [一般類型系統](./base-types/common-type-system.md)
*   [Common Language Specification](language-independence-and-language-independent-components.md)
