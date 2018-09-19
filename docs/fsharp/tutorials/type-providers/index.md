---
title: 型別提供者
description: '了解 F # 型別提供者的元件，可提供型別、 屬性和方法，以供您程式的方式。'
ms.date: 04/02/2018
ms.openlocfilehash: 5fa9de229caa2ec3ba4a248ca5cd1c8aa5adb230
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46287079"
---
# <a name="type-providers"></a>型別提供者

F# 型別提供者是一個元件，該元件會提供類型、屬性和方法讓您在程式中使用。 型別提供者會產生所謂**提供的型別**，這由 F # 編譯器產生，而且外部資料來源為基礎。

比方說，F # 型別提供者的 SQL 可以產生代表資料表和關聯式資料庫中的資料行的類型。 事實上，這是什麼[SQLProvider](https://fsprojects.github.io/SQLProvider/)型別提供者。

提供類型取決於型別提供者的輸入參數。 這類的輸入可以是範例資料來源 （例如 JSON 結構描述檔案），直接指向外部服務或資料來源的連接字串的 URL。 型別提供者也可以確保只會視情況下，展開類型的群組也就是說，它們會展開如果實際上您的程式所參考的型別。 這樣就能以強類型的方式視需要直接整合大型的資訊空間，例如線上資料市場。

## <a name="generative-and-erased-type-providers"></a>富有生產力和它們的型別提供者

型別提供者有兩種形式： 富有生產力和清除。

富有生產力的型別提供者會產生可以寫成.NET 類型，會產生這些組件的類型。 這可讓他們從其他組件中的程式碼取用。 這表示資料來源的型別的表示通常必須是另一個則是可行的方法是使用.NET 型別代表。

清除的型別提供者產生僅供在組件或專案，從產生的類型。 型別都是暫時的;也就是說，它們不會寫入至組件，而且不能使用的其他組件中的程式碼。 它們可以包含*延遲*成員，可讓您將使用提供的型別可能是無限的資訊空間中。 它們可用於使用大型且相互連結的資料來源的一小部分。

## <a name="commonly-used-type-providers"></a>常用的型別提供者

下列的廣泛使用程式庫包含型別提供者針對不同的使用者：

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/)的 JSON、 XML、 CSV 及 HTML 文件格式和資源，包含型別提供者。
- [根據 SQLProvider](https://fsprojects.github.io/SQLProvider/)提供強型別存取關聯資料庫物件的對應和 F # LINQ 對這些資料來源的查詢。
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)編譯時期的型別提供者的一組簽入內嵌的 F # 中的 T-SQL。
- [Azure 儲存體類型提供者](https://fsprojects.github.io/AzureStorageTypeProvider/)提供 Azure Blob、 資料表和佇列，可讓您存取這些資源，而不需要指定為字串，在整個程式的資源名稱的類型。
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html)包含**GraphQLProvider**，可由 URL 指定 GraphQL server 為基礎的類型。

必要時，您可以[建立您自己的自訂型別提供者](creating-a-type-provider.md)，或參考已由其他人建立的型別提供者。 例如，假設您的組織的資料服務提供大量且不斷增加的具名資料集，各資料集都有自己的穩定資料結構描述。 您可能選擇建立一個類型提供者，以強類型方式讀取結構描述並對程式設計人員呈現最新的可用資料集。

## <a name="see-also"></a>另請參閱

- [教學課程： 建立型別提供者](creating-a-type-provider.md)
- [F# 語言參考](../../language-reference/index.md)
- [Visual F#](../../index.md)
