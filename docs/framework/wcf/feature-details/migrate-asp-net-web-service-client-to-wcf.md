---
title: HOW TO：將 ASP.NET Web 服務用戶端程式碼移轉至 Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
ms.openlocfilehash: cb60f9cb2e8f35ee703b049eae9e3d99c1ec7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491126"
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>HOW TO：將 ASP.NET Web 服務用戶端程式碼移轉至 Windows Communication Foundation
下列程序會說明需要將 ASP.NET Web 服務用戶端程式碼移轉至 WCF 遵循的概略步驟。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>將 ASP.NET Web 服務用戶端程式碼移轉至 WCF  
  
1.  請確定已存有用戶端的一組完整測試。  
  
2.  使用 Visual Studio 2005 將用戶端應用程式升級到 .NET 2.0。 執行這組測試。  
  
3.  從用戶端專案移除 ASP.NET 用戶端程式碼。 該程式碼位於使用 WSDL.exe 工具產生的模組中。  
  
4.  產生 WCF 用戶端程式碼使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 將程式碼新增至用戶端專案，然後將組態輸出合併至用戶端現有的組態檔中。  
  
5.  編譯應用程式。 修復編譯錯誤之前的 ASP.NET 用戶端類型的參考取代為新的 WCF 用戶端類型的參考。  
  
6.  執行這組測試。  
  
## <a name="see-also"></a>另請參閱  
 [如何：將 ASP.NET Web 服務程式碼移轉至 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
