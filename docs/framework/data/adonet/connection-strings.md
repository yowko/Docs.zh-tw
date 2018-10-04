---
title: ADO.NET 中的連接字串
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 1e6e2b6870195c99279639e1f4576a30b7126d4d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583682"
---
# <a name="connection-strings-in-adonet"></a>ADO.NET 中的連接字串
.NET Framework 2.0 導入了使用連接字串的新功能，包括在連接字串產生器 (Builder) 類別 (Class) 中引入新的關鍵字，這麼做可在執行階段建立有效的連接字串。  
  
連接字串 (Connection String) 包含可當做參數從資料提供者 (Data Provider) 傳遞至資料來源的初始化資訊。 此語法會因資料提供者而不同，而且連接字串會在嘗試開啟連接期間進行剖析。 語法錯誤會產生執行階段例外狀況 (Exception)，但其他錯誤只會發生在資料來源接收連接資訊之後。 經過驗證後，資料來源便可套用在連接字串中指定的選項並開啟連接。
  
連接字串的格式是分號分隔的索引鍵/值參數組清單：
  
    keyword1=value; keyword2=value;
  
關鍵字不區分大小寫。 值，不過，可能會區分大小寫，根據資料來源。 關鍵字和值可能會包含[空白字元](https://en.wikipedia.org/wiki/Whitespace_character#Unicode)，但忽略關鍵字中並不具引號的開頭和尾端空白字元的值。

如果值包含分號[Unicode 控制字元](https://en.wikipedia.org/wiki/Unicode_control_characters)、 開頭或結尾的空白字元，它必須以單引號或雙引號括住，例如：

    Keyword=" whitespace  ";
    Keyword='special;character';

封入字元可能不會發生在其所包圍的值。 因此，只有在雙引號，反之亦然，可以用包含單引號的值：

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

引號本身，以及在等號，不需要逸出，因此下列連接字串是有效：

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

直到下一步 以分號或字串的結尾會讀取每個值，因為第二個範例中的值是`a=b=c`，最後的分號則是選擇性。

有效的連接字串語法隨提供者而異，且是從早期的 API (如 ODBC) 經過多年不斷發展而來的。 .NET Framework Data Provider for SQL Server (SqlClient) 納入了許多舊式語法項目，而且對一般連接字串語法通常都可接受。 連接字串語法項目經常會有同等效力的同義資料表 (Synonym)，但某些語法和拼字錯誤可能會導致問題。 例如，"`Integrated Security=true`" 有效，"`IntegratedSecurity=true`" 則會導致錯誤。 此外，在執行階段自未經驗證的使用者輸入所建構的連接字串可能會導致字串插入式攻擊，進而危及資料來源的安全性。
  
為了解決這些問題，ADO.NET 2.0 針對每個 .NET Framework 資料提供者導入新的連接字串產生器。 關鍵字會以屬性的方式公開 (Expose)，如此就可在將連接字串提交至資料來源之前先驗證字串語法。
  
## <a name="in-this-section"></a>本節內容  
 [連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 示範如何使用 `ConnectionStringBuilder` 類別在執行階段建構有效的連接字串。
  
 [連接字串和組態檔](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 示範如何在組態檔中儲存及擷取連接字串。
  
 [連接字串語法](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 說明如何針對`SqlClient`、`OracleClient`、`OleDb` 和 `Odbc` 設定提供者專用的連接字串。
  
 [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 示範的技術可保護用於連接至資料來源的資訊。
  
## <a name="see-also"></a>另請參閱  
 [連接至資料來源](/cpp/data/odbc/connecting-to-a-data-source)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
