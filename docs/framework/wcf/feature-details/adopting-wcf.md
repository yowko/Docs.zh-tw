---
title: 採用 Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: 40a2eac1e282640f0df70a7eca16e3b2401c0764
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546004"
---
# <a name="adopt-windows-communication-foundation"></a>採用 Windows Communication Foundation

您可以選擇使用 Windows Communication Foundation (WCF) 進行新的開發，同時繼續維護使用 ASP.NET 開發的現有應用程式。 因為 WCF 是為了促進與在任何案例中以 .NET Framework 所建立的應用程式進行通訊最適合的選擇，所以它可以作為標準工具，以 ASP.NET 無法解決各種不同的軟體通訊問題。

新的 WCF 應用程式可以部署在與現有 ASP.NET Web 服務相同的電腦上。 如果現有的 ASP.NET Web 服務使用2.0 版之前的 .NET Framework 版本，您可以使用 ASP.NET IIS 註冊工具，選擇性地將 .NET Framework 2.0 部署到要裝載新 WCF 應用程式的 IIS 應用程式。 該工具記載于 [ASP.NET Iis 註冊工具 ( # A0) ](/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90))，並在 iis 6.0 管理主控台中建立了一個使用者介面。

WCF 可以用來將新功能新增至現有的 ASP.NET Web 服務，方法是將設定為在 ASP.NET 相容性模式下執行的 WCF 服務加入至 IIS 中現有的 ASP.NET Web 服務應用程式。 由於 ASP.NET 的相容性模式，新 WCF 服務的程式碼可以使用類別來存取和更新與預先存在的 ASP.NET 程式碼相同的應用程式狀態資訊 <xref:System.Web.HttpContext> 。 應用程式也可以共用相同的類別庫。

WCF 用戶端可以使用 ASP.NET Web 服務。 使用設定的 WCF 服務 <xref:System.ServiceModel.BasicHttpBinding> 可供 ASP.NET Web 服務用戶端使用。 ASP.NET Web 服務可與 WCF 應用程式並存，而 WCF 甚至可以用來將功能新增至現有的 ASP.NET Web 服務。 由於所有這些方法都可以搭配使用 WCF 和 ASP.NET Web 服務，因此如果您需要 WCF 所提供的功能，而不是 ASP.NET Web 服務，您可能會想要將 ASP.NET Web 服務遷移至 WCF。

即使在需要的情況下，將程式碼從某個技術遷移至另一種技術並不是正確的方法。 採用新技術的原因，是為了符合無法與舊版技術達成的新需求，而且在這種情況下，正確的做法是設計新的解決方案，以符合新展開的需求集。 新設計的優點在於採用現有系統的經驗，以及設計該系統以來所獲取的智慧。 新設計也可以使用新技術的完整功能，而不必在新平台上重現舊設計。 將新設計的重要元素原型化之後，在新的系統內重複使用現有系統中的程式碼會變得更容易。

## <a name="see-also"></a>另請參閱

- [作法：擷取中繼資料並實作相容性服務](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
