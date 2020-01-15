---
title: 採用 Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: 53f51c6a93d4768d3aa158d44cb7d20f945393f5
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964249"
---
# <a name="adopting-windows-communication-foundation"></a>採用 Windows Communication Foundation

您可以選擇使用 Windows Communication Foundation （WCF）進行新的開發，同時繼續維護使用 ASP.NET 開發的現有應用程式。 因為 WCF 的目的是為了方便與使用 .NET Framework 在任何案例中建立的應用程式進行通訊，所以它可以做為解決各種不同軟體通訊問題的標準工具，使 ASP.NET因此.

新的 WCF 應用程式可以部署在與現有 ASP.NET Web 服務相同的電腦上。 如果現有的 ASP.NET Web 服務使用2.0 版之前的 .NET Framework 版本，您可以使用 ASP.NET IIS 註冊工具，選擇性地將 .NET Framework 2.0 部署到要裝載新 WCF 應用程式的 IIS 應用程式。 該工具記載于[ASP.NET Iis 註冊工具（Aspnet_regiis .exe）](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90))，並在 iis 6.0 管理主控台內建使用者介面。

WCF 可以藉由將設定為在 ASP.NET 相容性模式中執行的 WCF 服務新增至 IIS 中現有的 ASP.NET Web 服務應用程式，來將新功能加入至現有的 ASP.NET Web 服務。 由於 ASP.NET 的相容性模式，新 WCF 服務的程式碼可以使用 <xref:System.Web.HttpContext> 類別，存取和更新與預先存在的 ASP.NET 碼相同的應用程式狀態資訊。 應用程式也可以共用相同的類別庫。

WCF 用戶端可以使用 ASP.NET Web 服務。 使用 <xref:System.ServiceModel.BasicHttpBinding> 設定的 WCF 服務可供 ASP.NET Web 服務用戶端使用。 ASP.NET Web 服務可以與 WCF 應用程式共存，而 WCF 甚至可以用來將功能新增至現有的 ASP.NET Web 服務。 假設所有這些方法都可以搭配使用 WCF 和 ASP.NET Web 服務，則只有在需要 WCF 所提供的功能，而不是 ASP.NET Web 服務時，您才可以將 ASP.NET Web 服務遷移至 WCF。

即使在少數情況下，將程式碼從一項技術遷移至另一種技術並不是正確的方法。 採用新技術的原因在於符合使用稍早技術無法滿足的新需求，在該情況下，正確的做法是設計新的解決方案以符合一組新擴展的需求。 新設計的優點在於採用現有系統的經驗，以及設計該系統以來所獲取的智慧。 新設計也可以使用新技術的完整功能，而不必在新平台上重現舊設計。 製作新設計主要元素的原型之後，在新系統中重複使用現有系統的程式碼就會變得更容易。

## <a name="see-also"></a>請參閱

- [如何：擷取中繼資料並實作相容性服務](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
