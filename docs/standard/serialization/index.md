---
title: 序列化-.NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053352"
---
# <a name="serialization-in-net"></a>.NET 的序列化

序列化是將物件的狀態轉換成可保存或傳輸之形式的程序。 序列化的互補方法是還原序列化，它將資料流轉換成為物件。 這些程式一起允許儲存和傳輸資料。  
  
.NET 具備下列序列化技術：  
  
- [二進位序列化](binary-serialization.md)會保留型別精確度，這有助於在應用程式的不同調用之間保留物件的狀態。 例如，藉由將物件序列化至剪貼簿，就可在不同應用程式之間共用該物件。 您可以將物件序列化為資料流、序列化至磁碟、記憶體、在網路上序列化等等。 在遠端使用序列化從一台電腦或應用程式定義域，以「值」傳遞物件至他處。  
  
- [XML 和 SOAP 序列化](xml-and-soap-serialization.md)只會序列化公用屬性和欄位，不會保留型別精確度。 當您不想限制使用資料的應用程式，而能提供或使用資料時，這種做法就很有用。 因為 XML 為開放標準，因此是在 Web 上共用資料的很好選擇。 同樣是開放標準的 SOAP，也是一項很好的選擇。  
  
- [JSON 序列化](system-text-json-overview.md)只會序列化公用屬性，而且不會保留型別精確度。 JSON 是一種開放式標準，是在網路上共用資料的理想選擇。

## <a name="reference"></a>參考資料

<xref:System.Runtime.Serialization>  
包含類別，可以用來序列化和還原序列化物件。
  
<xref:System.Xml.Serialization>  
包含可用來將物件序列化為 XML 格式之文件或資料流的類別。

<xref:System.Text.Json>  
包含可以用來將物件序列化為 JSON 格式檔或資料流程的類別。
