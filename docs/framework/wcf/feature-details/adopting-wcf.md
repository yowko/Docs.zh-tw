---
title: 採用 Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: 5773d2687eb06cfc562dbe25fa9b94864b1b3a49
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217501"
---
# <a name="adopting-windows-communication-foundation"></a>採用 Windows Communication Foundation

您可以選擇使用新的程式開發的 Windows Communication Foundation (WCF)，而繼續維護現有的應用程式使用 ASP.NET 開發的。 WCF 的設計是要使用.NET Framework 中的任何案例建置應用程式簡化通訊最適合的選擇，因為它可做為標準的工具來解決各種軟體通訊問題的方式，讓 ASP.NET不能。

新的 WCF 應用程式可以部署與現有的 ASP.NET Web 服務的同一部電腦上。 如果現有的 ASP.NET Web 服務會使用.NET Framework 2.0 版之前的版本，您可以選擇性地將.NET Framework 2.0 部署至新的 WCF 應用程式要裝載的 IIS 應用程式使用 ASP.NET IIS 註冊工具。 該工具的說明位於[ASP.NET IIS 註冊工具 (Aspnet_regiis.exe)](https://go.microsoft.com/fwlink/?LinkId=94687)，和已建置到 IIS 6.0 管理主控台的使用者介面。

WCF 可以用來加入現有的 ASP.NET Web 服務中的新功能，加上設定為在 ASP.NET 相容性模式中執行現有的 ASP.NET Web 服務應用程式在 IIS 中的 WCF 服務中。 由於 ASP.NET 相容性模式中，新的 WCF 服務的程式碼可以存取與更新現有的 ASP.NET 程式碼中，相同的應用程式狀態資訊使用<xref:System.Web.HttpContext>類別。 應用程式也可以共用相同的類別庫。

WCF 用戶端可以使用 ASP.NET Web 服務。 使用所設定的 WCF 服務<xref:System.ServiceModel.BasicHttpBinding>可由 ASP.NET Web 服務用戶端。 ASP.NET Web 服務可以同時存在與 WCF 應用程式，並甚至可以使用 WCF 將功能加入至現有的 ASP.NET Web 服務。 假設這些所有方式可以一起使用 WCF 和 ASP.NET Web 服務，您可能都想要將 ASP.NET Web 服務移轉至 WCF，只有在需要 WCF 和不是 ASP.NET Web 服務所提供的功能。

甚至在需要在少數情況下，移轉的程式碼從一種技術之間很少是正確的方法。 採用新技術的原因在於符合使用稍早技術無法滿足的新需求，在該情況下，正確的做法是設計新的解決方案以符合一組新擴展的需求。 新設計的優點在於採用現有系統的經驗，以及設計該系統以來所獲取的智慧。 新設計也可以使用新技術的完整功能，而不必在新平台上重現舊設計。 製作新設計主要元素的原型之後，在新系統中重複使用現有系統的程式碼就會變得更容易。

## <a name="see-also"></a>另請參閱

- [如何：擷取中繼資料並實作相容性服務](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
