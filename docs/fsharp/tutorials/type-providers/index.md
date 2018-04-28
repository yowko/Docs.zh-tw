---
title: 型別提供者
description: '了解 F # 類型提供者的提供類型、 屬性和方法讓您的程式中使用的元件的方式。'
author: cartermp
ms.author: phcart
ms.date: 04/02/2018
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 5b7bae6f960b9cfa91188e8eb80be949cda12b65
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="type-providers"></a>型別提供者

F# 型別提供者是一個元件，該元件會提供類型、屬性和方法讓您在程式中使用。 型別提供者產生所謂**提供型別**，F # 編譯器所產生以及外部資料來源為基礎。

例如，F # 類型 SQL 的提供者可以產生型別代表資料表與關聯式資料庫中的資料行。 事實上，這是什麼[根據 SQLProvider](https://fsprojects.github.io/SQLProvider/)型別提供者。

提供類型取決於型別提供者的輸入參數。 這類的輸入可以是範例資料來源 （例如 JSON 結構描述檔案），直接指向外部服務或資料來源的連接字串的 URL。 型別提供者也可以確保類型群組只會展開視;也就是說，它們會展開如果您的程式實際參考類型。 這樣就能以強類型的方式視需要直接整合大型的資訊空間，例如線上資料市場。

## <a name="generative-and-erased-type-providers"></a>Generative 和清除的型別提供者

型別提供者有兩種形式： Generative 和清除。

Generative 型別提供者會產生可以寫成.NET 型別，會產生這些組件的類型。 這可讓它們使用從其他組件中的程式碼。 這表示資料來源的型別的表示通常必須是可搭配.NET 類型所代表的其中一個。

清除的型別提供者產生才可以使用組件或從產生的專案中的類型。 型別是暫時的。也就是說，它們不會寫入至組件，而且不能使用的其他組件中的程式碼。 它們可以包含*延遲*成員，可讓您將使用提供的型別從可能無限的資訊空間。 它們可用於使用很大且相互連結的資料來源的一小部分。

## <a name="commonly-used-type-providers"></a>常用的型別提供者

下列的廣泛使用程式庫包含型別提供者，針對不同的使用者：

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/)的 JSON、 XML、 CSV 及 HTML 文件格式和資源，包含型別提供者。
- [根據 SQLProvider](https://fsprojects.github.io/SQLProvider/)提供強型別存取透過物件對應和 F # LINQ 關聯資料庫對這些資料來源的查詢。
- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/)一組型別提供者的編譯時間檢查 T-SQL F # 中的內嵌。
- [Azure 儲存體的型別提供者](https://fsprojects.github.io/AzureStorageTypeProvider/)提供 Azure Blob、 資料表和佇列，可讓您存取這些資源，而不需要資源名稱指定為字串，在整個程式的類型。
- [FSharp.Data.GraphQL](https://fsprojects.github.io/FSharp.Data.GraphQL/index.html)包含**GraphQLProvider**，可由 URL 指定 GraphQL server 為基礎的類型。

在需要時，您可以[建立您自己的自訂型別提供者](creating-a-type-provider.md)，或參考其他人所建立的型別提供者。 例如，假設您的組織的資料服務提供大量且不斷增加的具名資料集，各資料集都有自己的穩定資料結構描述。 您可能選擇建立一個類型提供者，以強類型方式讀取結構描述並對程式設計人員呈現最新的可用資料集。

## <a name="see-also"></a>另請參閱
[教學課程： 建立型別提供者](creating-a-type-provider.md)

[F# 語言參考](../../language-reference/index.md)

[Visual F#](../../index.md)
