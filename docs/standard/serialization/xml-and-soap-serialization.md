---
title: XML 和 SOAP 序列化
description: 此總覽討論 XML 序列化，其可用來將物件序列化為符合 SOAP 規格的 XML 資料流程。
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: 6b7d6f59694a28207758fa7772781eed073917e4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379548"
---
# <a name="xml-and-soap-serialization"></a>XML 和 SOAP 序列化

XML 序列化會將物件的公用欄位和屬性，以及方法的參數和傳回值，轉換（序列化）為符合特定 XML 架構定義語言（XSD）檔的 XML 資料流程。 XML 序列化會產生強型別 (Strongly Typed) 類別，其中包含的公用屬性和欄位都轉換為序列格式 (此例為 XML) 以進行儲存或傳輸。

因為 XML 為開放標準，無論是何種平台，XML 資料流都可依需要由任何應用程式處理。 例如，使用 ASP.NET 建立的 XML Web 服務以 <xref:System.Xml.Serialization.XmlSerializer> 類別建立 XML 資料流，在網際網路或內部網路的 XML Web 服務應用程式之間傳遞資料。 相反地，還原序列化採用這樣的 XML 資料流並重建物件。

XML 序列化也可用來將物件序列化為與 SOAP 規格相符的 XML 資料流。 SOAP 是以 XML 為基礎的通訊協定，特別設計來傳輸使用 XML 的程序呼叫。

若要序列化或還原序列化物件，請使用 <xref:System.Xml.Serialization.XmlSerializer> 類別。 若要建立要序列化的類別，請使用 XML 結構描述定義工具。

## <a name="see-also"></a>請參閱

- [二進位序列化](binary-serialization.md)
- [使用 ASP.NET 和 XML Web Service 用戶端所建立的 XML Web 服務](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
