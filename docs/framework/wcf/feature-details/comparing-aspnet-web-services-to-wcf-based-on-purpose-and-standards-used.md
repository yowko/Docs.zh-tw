---
title: 依據用途與使用的標準來比較 ASP.NET Web 服務與 WCF
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: b27f3516868ec70319ce37fbbd774a29347b0bc8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597575"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>依據用途與使用的標準來比較 ASP.NET Web 服務與 WCF
ASP.NET Web 服務的設計目的為建置會透過 HTTP 使用簡易物件存取通訊協定 (Simple Object Access Protocol，SOAP)，傳送及接收訊息的應用程式。 可以使用 XML 結構描述來定義訊息的結構，也會提供工具提升在 .NET Framework 物件之間序列化訊息的速度。 這項技術可自動產生中繼資料以描述 Web 服務描述語言 (WSDL) 中的 Web 服務，接著提供第二個工具讓您可以從 WSDL 產生用於 Web 服務的用戶端。  
  
 WCF 可讓 .NET Framework 應用程式與其他軟體實體交換訊息。 預設會使用 SOAP，但訊息的格式則不受限制，並且可透過使用任何傳輸通訊協定來傳達這些訊息。 可以使用 XML 結構描述來定義訊息的結構，而且有多種選項可用來序列化 .NET Framework 物件之間的訊息。 WCF 可以自動產生中繼資料，以描述使用 WSDL 中的技術所建立的應用程式，而且也會提供工具從 WSDL 產生這些應用程式的用戶端。  
  
 ASP.NET Web 服務所支援的標準記載于[使用 ASP.NET 建立之 XML Web Service 的優點](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0859ebft(v=vs.100))。 由[系統提供的互通性系結所支援的 Web 服務通訊協定](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)中列出 WCF 支援的更廣泛的標準清單。  
  
## <a name="see-also"></a>請參閱

- [根據開發情況比較 ASP.NET Web 服務與 WCF](comparing-aspnet-web-services-to-wcf-based-on-development.md)
