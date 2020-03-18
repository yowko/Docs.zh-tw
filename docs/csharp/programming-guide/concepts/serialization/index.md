---
title: 序列化 (C#)
ms.date: 01/02/2020
ms.openlocfilehash: d914298a370b09307e84c88959542b4823cf37ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167591"
---
# <a name="serialization-c"></a>序列化 (C#)

序列化程序會將物件轉換成位元組資料流，以將物件儲存或傳輸到記憶體、資料庫或檔案。 其主要目的是儲存物件的狀態，這樣就能在需要時重新建立該物件。 反向的程序則稱為還原序列化。

## <a name="how-serialization-works"></a>序列化的運作方式

下圖顯示序列化的整體程序：

![序列化圖形](./media/index/serialization-process.gif)

物件序列化為傳輸資料的流。 流可能還包含有關物件類型的資訊，例如其版本、區域性和程式集名稱。 從該流中，物件可以存儲在資料庫、檔或記憶體中。

### <a name="uses-for-serialization"></a>序列化的用法

序列化允許開發人員保存物件的狀態並根據需要重新創建它，從而提供物件的存儲和資料交換。 通過序列化，開發人員可以執行以下操作：

* 使用 Web 服務將物件發送到遠端應用程式
* 將物件從一個域傳遞到另一個域
* 將物件作為 JSON 或 XML 字串通過防火牆傳遞
* 跨應用程式維護安全或特定于使用者的資訊

## <a name="json-serialization"></a>JSON 序列化

命名<xref:System.Text.Json>空間包含 JavaScript 物件符號 （JSON） 序列化和反序列化的類。 JSON 是一個開放的標準，通常用於通過網路共用資料。

JSON 序列化將物件的公共屬性序列化為符合[RFC 8259 JSON 規範的](https://tools.ietf.org/html/rfc8259)字串、位元組陣列或流。 要控制類實例<xref:System.Text.Json.JsonSerializer>的序列化或反序列化方式，可以：

* 使用<xref:System.Text.Json.JsonSerializerOptions>物件
* 將命名空間的屬性<xref:System.Text.Json.Serialization>應用於類或屬性
* [實現自訂轉換器](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>二進位與 XML 序列化

命名<xref:System.Runtime.Serialization>空間包含用於二進位和 XML 序列化和反序列化的類。

二進位序列化使用二進位編碼來產生精簡的序列化，適用於儲存或通訊端型網路資料流。 在二進位序列化中，系統會序列化所有成員 (即使是唯讀的成員)，且效能會增強。

XML 序列化會將物件的公用欄位和屬性，或是方法的參數和傳回值，序列化為與特定 XML 結構描述定義語言 (XSD) 文件相符的 XML 資料流。 XML 序列化會產生強型別的類別，其中包含的公用屬性和欄位都會轉換成 XML。 <xref:System.Xml.Serialization>包含用於序列化和反序列化 XML 的類。 您可以將屬性套用至類別和類別成員，以便控制 <xref:System.Xml.Serialization.XmlSerializer> 序列化或還原序列化類別執行個體的方式。

### <a name="making-an-object-serializable"></a>讓物件可序列化

對於二進位或 XML 序列化，您需要：

* 要序列化的物件
* 包含序列化物件的流
* <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName>實例

將<xref:System.SerializableAttribute>屬性應用於類型以指示類型實例可以序列化。 如果您嘗試序列化但該類型沒有 <xref:System.SerializableAttribute> 屬性，則會擲回例外狀況。

要防止欄位序列化，請應用該<xref:System.NonSerializedAttribute>屬性。 如果可序列化型別的欄位包含指標、控制代碼，或一些其他特定環境專屬的資料結構，且無法以有意義的方式在不同環境中重新建構該欄位，則您可能想要讓它成為不可序列化的。

如果序列化類別包含對其他類別之物件的參考，且該類別標記為 <xref:System.SerializableAttribute>，則系統也會將那些物件序列化。

### <a name="basic-and-custom-serialization"></a>基本和自訂序列化

二進位和XML序列化可以通過兩種方式執行，基本和自訂。

基本序列化使用 .NET Framework 來自動序列化物件。 唯一的要求是類已應用該<xref:System.SerializableAttribute>屬性。 可以使用 <xref:System.NonSerializedAttribute> 來防止特定欄位被序列化。

當您使用基本序列化時，物件的版本控制可能產生問題。 版本控制的問題很重要時，建議使用自訂序列化。 基本序列化是執行序列化最簡單的方式，但它對該程序提供的控制機制並不多。

在自訂序列化中，您可以明確指定要序列化的物件，以及序列化的方式。 類別必須標記為 <xref:System.SerializableAttribute> 並實作 <xref:System.Runtime.Serialization.ISerializable> 介面。 如果希望以自訂方式反序列化物件，請使用自訂建構函式。

## <a name="designer-serialization"></a>設計工具序列化

設計工具序列化是特殊格式的序列化，其中包含一種與開發工具相關聯的物件持續性。 設計工具序列化程序的作用是將物件圖形轉換成來源檔案，而該檔案稍後可用於復原物件圖形。 來源檔案可以包含程式碼、標記，或甚至 SQL 資料表資訊。

## <a name="BKMK_RelatedTopics"></a> 相關主題和範例  

[系統.文本.Json 概述](../../../../standard/serialization/system-text-json-overview.md)演示如何獲取`System.Text.Json`庫。

[如何在 .NET 中序列化和反序列化 JSON。](../../../../standard/serialization/system-text-json-how-to.md)
演示如何使用<xref:System.Text.Json.JsonSerializer>類讀取和寫入 JSON 的物件資料。

[逐步解說：在 Visual Studio 中保存物件 (#C)](walkthrough-persisting-an-object-in-visual-studio.md)  
示範序列化能如何用來保存物件在執行個體之間的資料，可讓您儲存值，並且在下次物件具現化時擷取它們。

[如何從 XML 檔 （C#） 讀取物件資料](how-to-read-object-data-from-an-xml-file.md)  
示範如何讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。

[如何將物件資料寫入 XML 檔 （C#）](how-to-write-object-data-to-an-xml-file.md)  
示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將來自某個類別的物件寫入 XML 檔案。
