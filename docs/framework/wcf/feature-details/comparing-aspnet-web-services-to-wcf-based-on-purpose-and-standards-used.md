---
title: "依據用途與使用的標準來比較 ASP.NET Web 服務與 WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3fec18cb93486dfe9d2b09582ad263d19b00617
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>依據用途與使用的標準來比較 ASP.NET Web 服務與 WCF
ASP.NET Web 服務的設計目的為建置會透過 HTTP 使用簡易物件存取通訊協定 (Simple Object Access Protocol，SOAP)，傳送及接收訊息的應用程式。 可以使用 XML 結構描述來定義訊息的結構，也會提供工具提升在 .NET Framework 物件之間序列化訊息的速度。 這項技術可自動產生中繼資料以描述 Web 服務描述語言 (WSDL) 中的 Web 服務，接著提供第二個工具讓您可以從 WSDL 產生用於 Web 服務的用戶端。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可用於啟用 .NET Framework 應用程式，用來與其他軟體實體交換訊息。 預設會使用 SOAP，但訊息的格式則不受限制，並且可透過使用任何傳輸通訊協定來傳達這些訊息。 可以使用 XML 結構描述來定義訊息的結構，而且有多種選項可用來序列化 .NET Framework 物件之間的訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可自動產生中繼資料以說明使用 WSDL 的技術所建置的應用程式，也會提供工具從 WSDL 產生這些應用程式的用戶端。  
  
 ASP.NET Web 服務所支援的標準記載於[Web 服務使用 ASP.NET 建立 XML](http://go.microsoft.com/fwlink/?LinkId=94872)。 更廣泛的支援的標準清單[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]列於[Web 服務之互通性繫結所支援的通訊協定](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)。  
  
## <a name="see-also"></a>另請參閱  
 [比較 ASP.NET Web 服務與 WCF 架構開發](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
