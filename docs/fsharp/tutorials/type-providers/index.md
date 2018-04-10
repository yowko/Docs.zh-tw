---
title: 型別提供者
description: '了解 F # 類型提供者的提供類型、 屬性和方法讓您的程式中使用的元件的方式。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 25697ef6-465e-4248-9de5-1d199d4a8b59
ms.openlocfilehash: f721b5b378bf70fb594cad66bd90bd96a0320ee2
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="type-providers"></a>型別提供者

> [!NOTE]
本指南從 F # 3.0 開始撰寫，而且將更新。  請參閱 [FSharp.Data](https://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。

F# 型別提供者是一個元件，該元件會提供類型、屬性和方法讓您在程式中使用。 類型提供者是 F# 3.0 支援中進行資訊豐富程式設計的重要部分。 資訊豐富程式設計的關鍵在於消除使用網際網路和時下企業環境中所找到各種資訊來源的障礙。 將資訊來源納入程式中的其中一項明顯障礙，就是需要以類型、屬性和方法來表示該資訊，才能在程式語言環境中使用。 手動撰寫這些類型相當耗時又難以維護。 一般替代方式是使用程式碼產生器將檔案加入您的專案中，不過，傳統程式碼產生類型無法與 F# 支援的程式設計探勘模式徹底整合，因為每次調整服務參考後，都必須取代產生的程式碼。

F# 類型提供者提供的類型通常取決於外部資訊來源。 例如，SQL 的 F# 類型提供者會提供直接處理您可存取的 SQL 資料庫資料表所需的類型、屬性和方法。 同樣地，WSDL Web 服務的類型提供者會提供直接處理任何 WSDL Web 服務所需的類型、屬性和方法。

F# 類型提供者所提供的一組類型、屬性和方法可能取決於程式碼中提供的參數。 例如，類型提供者可以根據連接字串或服務 URL 提供不同的類型。 如此一來，透過連接字串或 URL 提供的資訊空間就會直接整合到程式中。 類型提供者也可以確保類型群組只會視需求展開，也就是說，如果您的程式實際參考類型，類型才會展開。 這樣就能以強類型的方式視需要直接整合大型的資訊空間，例如線上資料市場。

F# 包含數個內建的類型提供者，可供常用的網際網路和企業資料服務使用。 這些類型提供者可提供簡單的一般 SQL 關聯式資料庫及網路 OData 和 WSDL 服務的存取，並支援對這些資料來源使用 F# LINQ 查詢。

在需要時，您可以建立自己的自訂類型提供者，或是其他人所建立的參考類型提供者。 例如，假設您的組織的資料服務提供大量且不斷增加的具名資料集，各資料集都有自己的穩定資料結構描述。 您可能選擇建立一個類型提供者，以強類型方式讀取結構描述並對程式設計人員呈現最新的可用資料集。


## <a name="related-topics"></a>相關主題


|標題|描述|
|-----|-----------|
|[逐步解說：使用型別提供者存取 SQL 資料庫](accessing-a-sql-database.md)|說明如何使用 SqlDataConnection 型別提供者，根據直接連接資料庫的連接字串存取 SQL 資料庫的資料表和預存程序。 存取是使用 LINQ to SQL 對應。|
|[逐步解說：使用型別提供者和實體存取 SQL 資料庫](accessing-a-sql-database-entities.md)|說明如何使用 SqlEntityConnection 型別提供者，根據直接連接資料庫的連接字串存取 SQL 資料庫的資料表和預存程序。 存取是使用 LINQ to Entities 對應。 這個方法適用所有資料庫，但是所示範的範例是 SQL Server。|
|[逐步解說：使用型別提供者存取 OData 服務](accessing-an-odata-service.md)|說明如何使用 ODataService 型別提供者，根據服務 URL 以強類型的方式存取 OData 服務。|
|[逐步解說：使用型別提供者存取 Web 服務](accessing-a-web-service.md)|說明如何使用 WsdlService 型別提供者，根據服務 URL 以強類型的方式存取 WSDL Web 服務。|
|[逐步解說：從 DBML 檔案產生 F# 類型](generating-fsharp-types-from-dbml.md)|說明如何使用 DbmlFile 型別提供者，根據提供 Linq to SQL 資料庫結構描述規格的 DBML 檔案，存取 SQL 資料庫的資料表和預存程序。|
|[逐步解說：從 EDMX 結構描述檔案產生 F# 類型](generating-fsharp-types-from-edmx.md)|說明如何使用 EdmxFile 型別提供者，根據提供 Entity Framework 結構描述規格的 EDMX 檔案，存取 SQL 資料庫的資料表和預存程序。|
|[教學課程：建立型別提供者](creating-a-type-provider.md)|提供關於撰寫自己的自訂型別提供者的資訊。|
|[型別提供者安全性](type-provider-security.md)|提供開發型別提供者時的安全性考量相關資訊。|
|[類型提供者疑難排解](troubleshooting-type-providers.md)|提供使用型別提供者時可能發生之常見問題的相關資訊，並且包括解決方案的建議。|

## <a name="see-also"></a>請參閱
[F# 語言參考](../../language-reference/index.md)

[Visual F#](../../index.md)
