---
title: 採用 Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: bcd6543e6cd47dc723b308acebec6f492fa14fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="adopting-windows-communication-foundation"></a>採用 Windows Communication Foundation
您可以選擇進行新開發，使用 Windows Communication Foundation (WCF)，而繼續維護現有應用程式使用 ASP.NET 開發。 WCF 要用最適合的選擇，在任何案例中的.NET framework 建置之應用程式簡化通訊，因為它可以做為用來解決各種軟體通訊問題的方式的標準工具 ASP.NET不能。  
  
 可以為現有的 ASP.NET Web 服務相同的電腦上部署新的 WCF 應用程式。 如果現有的 ASP.NET Web 服務會使用.NET Framework 2.0 版之前的版本，您可以選擇性地將.NET Framework 2.0 部署至新的 WCF 應用程式要裝載的 IIS 應用程式使用 ASP.NET IIS 註冊工具。 該工具已記錄在[ASP.NET IIS 註冊工具 (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687)，和已建置到 IIS 6.0 管理主控台的使用者介面。  
  
 WCF 可以用來加入設定為在 IIS 中的現有 ASP.NET Web 服務應用程式在 ASP.NET 相容性模式中執行的 WCF 服務，將新功能加入至現有的 ASP.NET Web 服務。 由於 ASP.NET 相容性模式中，新的 WCF 服務的程式碼可以存取與更新相同的應用程式狀態資訊已存在的 ASP.NET 程式碼使用<xref:System.Web.HttpContext>類別。 應用程式也可以共用相同的類別庫。  
  
 WCF 用戶端可以使用 ASP.NET Web 服務。 使用所設定的 WCF 服務<xref:System.ServiceModel.BasicHttpBinding>可由 ASP.NET Web 服務用戶端。 與 WCF 應用程式，可以共存 ASP.NET Web 服務和 WCF 甚至可以將功能加入現有的 ASP.NET Web 服務使用。 假設這些所有方式可以一起使用 WCF 和 ASP.NET Web 服務，您可能都想要將 ASP.NET Web 服務移轉至 WCF 中，只有在需要 WCF 和不是 ASP.NET Web 服務所提供的功能。  
  
 即使是在少數必要的情況下，謹慎考慮將程式碼在兩個技術之間移轉也不見得是正確的方法。 採用新技術的原因在於符合使用稍早技術無法滿足的新需求，在該情況下，正確的做法是設計新的解決方案以符合一組新擴展的需求。 新設計的優點在於採用現有系統的經驗，以及設計該系統以來所獲取的智慧。 新設計也可以使用新技術的完整功能，而不必在新平台上重現舊設計。 製作新設計主要元素的原型之後，在新系統中重複使用現有系統的程式碼就會變得更容易。  
  
 在少數情況下從 ASP.NET Web 服務移轉至 WCF 其中為正確的解決方案下, 一節提供一些指引要如何繼續執行。 其中包含如何移轉服務以及如何移轉用戶端的建議。  
  
 如需如何將現有的 ASP.NET Web 服務移轉至 WCF 完整分析，請參閱[ASP.NET Web 服務和 Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761)。 本章節描述如何為您的 ASP.NET Web 服務，實作相容的 WCF 服務的中繼資料以及如何將 ASP.NET Web 服務和用戶端程式碼移轉至 WCF。  
  
## <a name="see-also"></a>另請參閱  
 [如何：擷取中繼資料並實作相容性服務](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [如何：將 ASP.NET Web 服務程式碼移轉至 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [如何：將 ASP.NET Web 服務用戶端程式碼移轉至 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
