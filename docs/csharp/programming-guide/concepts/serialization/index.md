---
title: 序列化 (C#)
ms.date: 01/02/2020
ms.openlocfilehash: b2532ccf281fdfaa951d56675066f1e239f9f480
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241977"
---
# <a name="serialization-c"></a>序列化 (C#)

序列化程序會將物件轉換成位元組資料流，以將物件儲存或傳輸到記憶體、資料庫或檔案。 其主要目的是儲存物件的狀態，這樣就能在需要時重新建立該物件。 反向的程序則稱為還原序列化。

## <a name="how-serialization-works"></a>序列化的運作方式

下圖顯示序列化的整體程序：

![序列化圖形](./media/index/serialization-process.gif)

物件會序列化為攜帶資料的資料流程。 資料流程可能也會有物件類型的相關資訊，例如其版本、文化特性和元件名稱。 從該資料流程，物件可以儲存在資料庫、檔案或記憶體中。

### <a name="uses-for-serialization"></a>序列化的用法

序列化可讓開發人員儲存物件的狀態，並視需要重新建立，提供物件的儲存以及資料交換。 藉由序列化，開發人員可以執行下列動作：

* 使用 web 服務將物件傳送至遠端應用程式
* 將一個或多個網域的物件傳遞給另一個
* 透過防火牆傳遞物件作為 JSON 或 XML 字串
* 維護應用程式間的安全性或使用者特定資訊

## <a name="json-serialization"></a>JSON 序列化

<xref:System.Text.Json>命名空間包含 JavaScript 物件標記法（JSON）序列化和還原序列化的類別。 JSON 是一種開放式標準，通常用來在網路上共用資料。

JSON 序列化會將物件的公用屬性序列化為符合[RFC 8259 JSON 規格](https://tools.ietf.org/html/rfc8259)的字串、位元組陣列或資料流程。 若要控制序列化 <xref:System.Text.Json.JsonSerializer> 或還原序列化類別實例的方式：

* 使用 <xref:System.Text.Json.JsonSerializerOptions> 物件
* 將命名空間中的屬性套用 <xref:System.Text.Json.Serialization> 至類別或屬性
* [執行自訂轉換器](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>二進位與 XML 序列化

<xref:System.Runtime.Serialization>命名空間包含二進位和 XML 序列化和還原序列化的類別。

二進位序列化使用二進位編碼來產生精簡的序列化，適用於儲存或通訊端型網路資料流。 在二進位序列化中，系統會序列化所有成員 (即使是唯讀的成員)，且效能會增強。

XML 序列化會將物件的公用欄位和屬性，或是方法的參數和傳回值，序列化為與特定 XML 結構描述定義語言 (XSD) 文件相符的 XML 資料流。 XML 序列化會產生強型別的類別，其中包含的公用屬性和欄位都會轉換成 XML。 <xref:System.Xml.Serialization>包含用來序列化和還原序列化 XML 的類別。 您可以將屬性套用至類別和類別成員，以便控制 <xref:System.Xml.Serialization.XmlSerializer> 序列化或還原序列化類別執行個體的方式。

### <a name="making-an-object-serializable"></a>讓物件可序列化

針對二進位或 XML 序列化，您需要：

* 要序列化的物件
* 包含序列化物件的資料流程
* <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName>實例

將 <xref:System.SerializableAttribute> 屬性套用至類型，以指出可以序列化類型的實例。 如果您嘗試序列化但該類型沒有 <xref:System.SerializableAttribute> 屬性，則會擲回例外狀況。

若要防止將欄位序列化，請套用 <xref:System.NonSerializedAttribute> 屬性。 如果可序列化型別的欄位包含指標、控制代碼，或一些其他特定環境專屬的資料結構，且無法以有意義的方式在不同環境中重新建構該欄位，則您可能想要讓它成為不可序列化的。

如果序列化類別包含對其他類別之物件的參考，且該類別標記為 <xref:System.SerializableAttribute>，則系統也會將那些物件序列化。

### <a name="basic-and-custom-serialization"></a>基本和自訂序列化

二進位和 XML 序列化可以透過兩種方式來執行：基本和自訂。

基本序列化會使用 .NET 自動序列化物件。 唯一的要求是類別已套用 <xref:System.SerializableAttribute> 屬性。 可以使用 <xref:System.NonSerializedAttribute> 來防止特定欄位被序列化。

當您使用基本序列化時，物件的版本控制可能產生問題。 版本控制的問題很重要時，建議使用自訂序列化。 基本序列化是執行序列化最簡單的方式，但它對該程序提供的控制機制並不多。

在自訂序列化中，您可以明確指定要序列化的物件，以及序列化的方式。 類別必須標記為 <xref:System.SerializableAttribute> 並實作 <xref:System.Runtime.Serialization.ISerializable> 介面。 如果您也想要以自訂方式還原序列化物件，請使用自訂的函式。

## <a name="designer-serialization"></a>設計工具序列化

設計工具序列化是特殊格式的序列化，其中包含一種與開發工具相關聯的物件持續性。 設計工具序列化程序的作用是將物件圖形轉換成來源檔案，而該檔案稍後可用於復原物件圖形。 來源檔案可以包含程式碼、標記，或甚至 SQL 資料表資訊。

## <a name="related-topics-and-examples"></a><a name="BKMK_RelatedTopics"></a> 相關主題和範例  

[System.web. Text. Json 總覽](../../../../standard/serialization/system-text-json-overview.md)說明如何取得連結 `System.Text.Json` 庫。

[如何在 .net 中序列化和還原序列化 JSON](../../../../standard/serialization/system-text-json-how-to.md)。
示範如何使用類別，在 JSON 中讀取和寫入物件資料 <xref:System.Text.Json.JsonSerializer> 。

[逐步解說：在 Visual Studio 中保存物件 (#C)](walkthrough-persisting-an-object-in-visual-studio.md)  
示範序列化能如何用來保存物件在執行個體之間的資料，可讓您儲存值，並且在下次物件具現化時擷取它們。

[如何從 XML 檔案讀取物件資料（c #）](how-to-read-object-data-from-an-xml-file.md)  
示範如何讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。

[如何將物件資料寫入 XML 檔案（c #）](how-to-write-object-data-to-an-xml-file.md)  
示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將來自某個類別的物件寫入 XML 檔案。
