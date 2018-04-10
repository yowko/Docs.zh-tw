---
title: 序列化 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67379a76-5465-4af8-a781-0b0b25a62d9a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 43e3be09a66ca1fef4f6a5b829c3057d2740d9c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="serialization-visual-basic"></a>序列化 (Visual Basic)
序列化程序會將物件轉換成位元組資料流，以將物件儲存或傳輸到記憶體、資料庫或檔案。 其主要目的是儲存物件的狀態，這樣就能在需要時重新建立該物件。 反向的程序則稱為還原序列化。  
  
## <a name="how-serialization-works"></a>序列化的運作方式  
 下圖顯示序列化的整體程序。  
  
 ![序列化圖形](../../../../csharp/programming-guide/concepts/serialization/media/serialization.gif "序列化")  
  
 物件會序列化成資料流，且其中不只包含資料，還有物件型別 (版本、文化特性及組件名稱) 的資訊。 而該資料流可以儲存在資料庫、檔案或記憶體中。  
  
### <a name="uses-for-serialization"></a>序列化的用法  
 序列化讓開發人員能夠儲存物件的狀態，並在需要時重新建立它，因此提供儲存物件及交換資料的功能。 藉由序列化，開發人員可以執行的動作如下：透過 Web 服務將物件傳送到遠端應用程式、將物件從一個網域傳遞到另一個網域、將物件以 XML 字串傳遞通過防火牆，或是跨應用程式維護安全性或使用者專屬資訊。  
  
### <a name="making-an-object-serializable"></a>讓物件可序列化  
 若要將物件序列化，您需要將要序列化的物件、將包含序列化物件的資料流，以及 <xref:System.Runtime.Serialization.Formatter>。 <xref:System.Runtime.Serialization> 包含序列化及還原序列化物件所需的類別。  
  
 將 <xref:System.SerializableAttribute> 屬性套用至某個類型，以表示此類型的執行個體為可序列化。 如果您嘗試序列化但該類型沒有 <xref:System.SerializableAttribute> 屬性，則會擲回 <xref:System.Runtime.Serialization.SerializationException> 例外狀況。  
  
 如果您不要將類別中的某個欄位序列化，請套用 <xref:System.NonSerializedAttribute> 屬性。 如果可序列化型別的欄位包含指標、控制代碼，或一些其他特定環境專屬的資料結構，且無法以有意義的方式在不同環境中重新建構該欄位，則您可能想要讓它成為不可序列化的。  
  
 如果序列化類別包含對其他類別之物件的參考，且該類別標記為 <xref:System.SerializableAttribute>，則系統也會將那些物件序列化。  
  
## <a name="binary-and-xml-serialization"></a>二進位與 XML 序列化  
 二進位或 XML 序列化都能使用。 在二進位序列化中，系統會序列化所有成員 (即使是唯讀的成員)，且效能會增強。 XML 序列化提供可讀性較高的程式碼，也會基於互通性目的為物件共用和使用方式提供更大的彈性。  
  
### <a name="binary-serialization"></a>二進位序列化  
 二進位序列化使用二進位編碼來產生精簡的序列化，適用於儲存或通訊端型網路資料流。  
  
### <a name="xml-serialization"></a>XML 序列化  
 XML 序列化會將物件的公用欄位和屬性，或是方法的參數和傳回值，序列化為與特定 XML 結構描述定義語言 (XSD) 文件相符的 XML 資料流。 XML 序列化會產生強型別的類別，其中包含的公用屬性和欄位都會轉換成 XML。 <xref:System.Xml.Serialization> 包含序列化及還原序列化 XML 所需的類別。  
  
 您可以將屬性套用至類別和類別成員，以便控制 <xref:System.Xml.Serialization.XmlSerializer> 序列化或還原序列化類別執行個體的方式。  
  
## <a name="basic-and-custom-serialization"></a>基本和自訂序列化  
 有兩種方式可以執行序列化：基本和自訂。 基本序列化使用 .NET Framework 來自動序列化物件。  
  
### <a name="basic-serialization"></a>基本序列化  
 基本序列化的唯一需求是物件已套用 <xref:System.SerializableAttribute> 屬性。 可以使用 <xref:System.NonSerializedAttribute> 來防止特定欄位被序列化。  
  
 如果使用基本序列化，物件的版本控制可能會產生問題，這種情況則較適合使用自訂序列化。 基本序列化是執行序列化最簡單的方式，但它對該程序提供的控制機制並不多。  
  
### <a name="custom-serialization"></a>自訂序列化  
 在自訂序列化中，您可以明確指定要序列化的物件，以及序列化的方式。 類別必須標記為 <xref:System.SerializableAttribute> 並實作 <xref:System.Runtime.Serialization.ISerializable> 介面。  
  
 如果您也想讓物件以自訂方式還原序列化，就必須使用自訂建構函式。  
  
## <a name="designer-serialization"></a>設計工具序列化  
 設計工具序列化是特殊格式的序列化，其中包含一種通常與開發工具相關聯的物件持續性。 設計工具序列化程序的作用是將物件圖形轉換成來源檔案，而該檔案稍後可用於復原物件圖形。 來源檔案可以包含程式碼、標記，或甚至 SQL 資料表資訊。  
  
##  <a name="BKMK_RelatedTopics"></a> 相關主題和範例  
 [逐步解說：在 Visual Studio 中保存物件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 示範序列化能如何用來保存物件在執行個體之間的資料，可讓您儲存值，並且在下次物件具現化時擷取它們。  
  
 [如何：從 XML 檔案讀取物件資料 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 示範如何讀取先前使用 <xref:System.Xml.Serialization.XmlSerializer> 類別來寫入 XML 檔案的物件資料。  
  
 [如何：將物件資料寫入 XML 檔案 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，將來自某個類別的物件寫入 XML 檔案。
