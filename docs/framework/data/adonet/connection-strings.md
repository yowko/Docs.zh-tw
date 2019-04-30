---
title: ADO.NET 中的連接字串
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 1197335f3ba2a09b6e7303d31bc32383d1fd3436
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032750"
---
# <a name="connection-strings-in-adonet"></a>ADO.NET 中的連接字串

連接字串 (Connection String) 包含可當做參數從資料提供者 (Data Provider) 傳遞至資料來源的初始化資訊。 此資料提供者接收的連接字串的值為<xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>屬性。 提供者剖析連接字串，並可確保語法正確，且所支援的關鍵字。 則<xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType>方法會將已剖析的連接參數傳遞至資料來源。 資料來源會執行進一步的驗證，以及建立連線。

## <a name="connection-string-syntax"></a>連接字串語法

連接字串是以分號分隔清單的索引鍵/值參數組：

    keyword1=value; keyword2=value;

關鍵字不區分大小寫。 值，不過，可能會區分大小寫，根據資料來源。 關鍵字和值可能會包含[空白字元](https://en.wikipedia.org/wiki/Whitespace_character#Unicode)。 前置和尾端空白字元是忽略關鍵字中並不具引號的值。

如果值包含分號[Unicode 控制字元](https://en.wikipedia.org/wiki/Unicode_control_characters)，或前置或尾端空格，它必須以單引號或雙引號括起來。 例如：

    Keyword=" whitespace  ";
    Keyword='special;character';

封入字元可能不會發生在其所包圍的值。 因此，只有在雙引號括住，反之亦然，可以用包含單引號的值：

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

引號本身，以及在等號，不需要逸出，因此下列連接字串是有效：

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

直到下一步 以分號或字串的結尾會讀取每個值，因為第二個範例中的值是`a=b=c`，最後的分號則是選擇性。

所有連接字串會都共用相同的基本語法，上面所述。 提供者而定，不過，可辨識的關鍵字集合，以及發展多年來從早期的 Api 中這類*ODBC*。 *.NET Framework*資料提供者*SQL Server* (`SqlClient`) 支援許多的關鍵字，從較舊的 Api，但通常較具彈性且接受許多常見的連接字串的同義字關鍵字。

輸入錯誤，可能會導致錯誤。 例如，`Integrated Security=true`有效，但`IntegratedSecurity=true`會造成錯誤。

從未經驗證的使用者輸入的執行階段以手動方式建構的連接字串受到字串插入式攻擊，並危及安全性，在資料來源。 為了解決這些問題中， *ADO.NET* 2.0 導入了[連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)每個 *.NET Framework*資料提供者。 這些連接字串產生器參數為強型別屬性，公開 （expose），並使它能夠傳送到資料來源之前，驗證連接字串。

## <a name="in-this-section"></a>本節內容

[連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)\
示範如何使用 `ConnectionStringBuilder` 類別在執行階段建構有效的連接字串。

[連接字串和組態檔](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)\
示範如何在組態檔中儲存及擷取連接字串。

[連接字串語法](../../../../docs/framework/data/adonet/connection-string-syntax.md)\
說明如何針對`SqlClient`、`OracleClient`、`OleDb` 和 `Odbc` 設定提供者專用的連接字串。

[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)\
示範的技術可保護用於連接至資料來源的資訊。

## <a name="see-also"></a>另請參閱

- [連接至資料來源](/cpp/data/odbc/connecting-to-a-data-source)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
