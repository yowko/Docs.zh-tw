---
title: 型別提供者
description: '瞭解 F # 型別提供者如何提供類型、屬性和方法，以便在您的程式中使用。'
ms.date: 04/02/2018
ms.openlocfilehash: eae64d2e318ee93f0b8d5b91f0c6da6c91743527
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202103"
---
# <a name="type-providers"></a>型別提供者

F# 型別提供者是一個元件，該元件會提供類型、屬性和方法讓您在程式中使用。 型別提供者會產生所謂的「**提供類型**」，這是由 F # 編譯器所產生，而且是以外部資料源為基礎。

例如，適用于 SQL 的 F # 類型提供者可以產生類型，代表關係資料庫中的資料表和資料行。 事實上，這就是[SQLProvider](https://fsprojects.github.io/SQLProvider/)型別提供者的功能。

提供的類型取決於型別提供者的輸入參數。 這類輸入可以是範例資料來源（例如 JSON 架構檔案）、直接指向外部服務的 URL，或是資料來源的連接字串。 型別提供者也可以確保類型的群組只視需要展開;也就是說，如果您的程式實際參考型別，它們就會展開。 這樣就能以強類型的方式視需要直接整合大型的資訊空間，例如線上資料市場。

## <a name="generative-and-erased-type-providers"></a>有生產力和已清除的類型提供者

型別提供者有兩種形式：有生產力和清除。

有生產力類型提供者會產生可當做 .NET 類型寫入至產生它們之元件中的類型。 這可讓它們從其他元件中的程式碼使用。 這表示，資料來源的具類型標記法通常必須是可以用 .NET 類型來表示的一種。

清除類型提供者會產生只能在其產生來源的元件或專案中使用的類型。 這些類型是暫時的;也就是說，它們不會寫入元件中，而且無法由其他元件中的程式碼使用。 它們可以包含*延遲*的成員，讓您可以從可能的無限資訊空間使用提供的類型。 它們對於使用大型且相互連接之資料來源的小型子集很有用。

## <a name="commonly-used-type-providers"></a>常用的類型提供者

下列廣泛使用的程式庫包含不同用途的類型提供者：

- [Fsharp.core：資料](https://fsharp.github.io/FSharp.Data/)報括 JSON、XML、CSV 和 HTML 檔案格式和資源的類型提供者。
- [SQLProvider](https://fsprojects.github.io/SQLProvider/)透過物件對應和 F # LINQ 查詢針對這些資料來源，提供關聯資料庫的強型別存取。
- [Fsharp.core。 SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)具有一組類型提供者，可用於在 F # 中檢查 t-sql 的編譯階段。
- [Azure 儲存體類型提供者](https://fsprojects.github.io/AzureStorageTypeProvider/)提供適用于 Azure Blob、資料表和佇列的類型，可讓您存取這些資源，而不需要在整個程式中將資源名稱指定為字串。
- [GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html)包含**GraphQLProvider**，它會根據 URL 所指定的 GraphQL 伺服器提供類型。

必要時，您可以[建立自己的自訂類型提供者](creating-a-type-provider.md)，或已由其他人建立的參考型別提供者。 例如，假設您的組織的資料服務提供大量且不斷增加的具名資料集，各資料集都有自己的穩定資料結構描述。 您可能選擇建立一個類型提供者，以強類型方式讀取結構描述並對程式設計人員呈現最新的可用資料集。

## <a name="see-also"></a>另請參閱

- [教學課程：建立類型提供者](creating-a-type-provider.md)
- [F # 語言參考](../../language-reference/index.md)
