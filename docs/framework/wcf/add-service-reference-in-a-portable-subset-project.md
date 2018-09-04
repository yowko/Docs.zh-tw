---
title: 將服務參考加入至可攜式子集專案
ms.date: 03/30/2017
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
ms.openlocfilehash: efe95a326e7c13237c7d2d74888c85bf919ed287
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542306"
---
# <a name="add-service-reference-in-a-portable-subset-project"></a><span data-ttu-id="1c569-102">將服務參考加入至可攜式子集專案</span><span class="sxs-lookup"><span data-stu-id="1c569-102">Add Service Reference in a Portable Subset Project</span></span>
<span data-ttu-id="1c569-103">可攜式子集專案可讓.NET 組件的程式設計人員維護單一來源樹狀結構，並建置系統，同時仍可支援多個.NET 實作 （桌上型電腦、 Silverlight、 Windows Phone 和 XBOX）。</span><span class="sxs-lookup"><span data-stu-id="1c569-103">Portable subset projects enable .NET assembly programmers to maintain a single source tree and build system while still supporting multiple .NET implementations (desktop, Silverlight, Windows Phone, and XBOX).</span></span> <span data-ttu-id="1c569-104">可攜式子集專案僅參考也就是可以使用任何.NET 實作的.NET framework 組件的.NET 可攜式程式庫。</span><span class="sxs-lookup"><span data-stu-id="1c569-104">Portable subset projects only reference .NET portable libraries which are a .NET framework assembly that can be used on any .NET implementation.</span></span>  
  
## <a name="add-service-reference-details"></a><span data-ttu-id="1c569-105">加入服務參考詳細資料</span><span class="sxs-lookup"><span data-stu-id="1c569-105">Add Service Reference Details</span></span>  
 <span data-ttu-id="1c569-106">將服務參考加入至可攜式子集專案時會強制執行下列限制：</span><span class="sxs-lookup"><span data-stu-id="1c569-106">When adding a service reference in a portable subset project the following restrictions are enforced:</span></span>  
  
1.  <span data-ttu-id="1c569-107"><xref:System.Xml.Serialization.XmlSerializer> 只能使用常值編碼。</span><span class="sxs-lookup"><span data-stu-id="1c569-107">For <xref:System.Xml.Serialization.XmlSerializer>, only literal encodings are allowed.</span></span> <span data-ttu-id="1c569-108">SOAP 編碼會在匯出期間產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c569-108">SOAP encodings generate an error during import.</span></span>  
  
2.  <span data-ttu-id="1c569-109">對於使用 <xref:System.Runtime.Serialization.DataContractSerializer> 案例的服務，會提供資料合約 Surrogate 以確保重複使用的型別只能來自可攜式子集。</span><span class="sxs-lookup"><span data-stu-id="1c569-109">For services that use <xref:System.Runtime.Serialization.DataContractSerializer> scenarios, a data contract surrogate is provided to ensure that reused types come only from the portable subset.</span></span>  
  
3.  <span data-ttu-id="1c569-110">可攜式程式庫不支援需要依賴繫結的端點 (所有繫結，但是不包括 <xref:System.ServiceModel.BasicHttpBinding>、沒有交易流程的 <xref:System.ServiceModel.WSHttpBinding>、可靠工作階段或 MTOM 編碼和對等的自訂繫結)，將會被忽略。</span><span class="sxs-lookup"><span data-stu-id="1c569-110">Endpoints which rely on bindings not supported in portable libraries (all bindings except <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> without transaction flow, reliable sessions, or MTOM encoding, and equivalent custom bindings) are ignored.</span></span>  
  
4.  <span data-ttu-id="1c569-111">在匯出之前，會刪除所有作業中全部訊息描述之訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="1c569-111">Message headers are deleted from all message descriptions in all operations before import.</span></span>  
  
5.  <span data-ttu-id="1c569-112">會從產生的用戶端 Proxy 程式碼中移除非可攜式屬性 <xref:System.ComponentModel.DesignerCategoryAttribute>、<xref:System.SerializableAttribute> 和 <xref:System.ServiceModel.TransactionFlowAttribute>。</span><span class="sxs-lookup"><span data-stu-id="1c569-112">Non-portable attributes <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, and <xref:System.ServiceModel.TransactionFlowAttribute> are removed from generated client proxy code.</span></span>  
  
6.  <span data-ttu-id="1c569-113">會從 <xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.OperationContractAttribute> 和 <xref:System.ServiceModel.FaultContractAttribute> 中移除非可攜式屬性 ProtectionLevel、SessionMode、IsInitiating 和 IsTerminating。</span><span class="sxs-lookup"><span data-stu-id="1c569-113">Non-portable properties ProtectionLevel, SessionMode, IsInitiating, IsTerminating are removed from <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, and <xref:System.ServiceModel.FaultContractAttribute>.</span></span>  
  
7.  <span data-ttu-id="1c569-114">所有服務作業都會產生為用戶端 Proxy 上的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="1c569-114">All service operations are generated as asynchronous operations on the client proxy.</span></span>  
  
8.  <span data-ttu-id="1c569-115">會將所產生且使用非可攜式型別的用戶端建構函式移除。</span><span class="sxs-lookup"><span data-stu-id="1c569-115">Generated client constructors which use non-portable types are removed.</span></span>  
  
9. <span data-ttu-id="1c569-116"><xref:System.Net.CookieContainer> 執行個體會在產生的用戶端上公開。</span><span class="sxs-lookup"><span data-stu-id="1c569-116">A <xref:System.Net.CookieContainer> instance is exposed on the generated client.</span></span>  
  
10. <span data-ttu-id="1c569-117">會在識別程式碼產生器組件及版本的檔案頂端插入註解：`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="1c569-117">A comment is inserted at the top of the file identifying the assembly and version of the code generator:`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`</span></span>  
  
11. <span data-ttu-id="1c569-118">不支援 <xref:System.Runtime.Serialization.ISerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="1c569-118">The <xref:System.Runtime.Serialization.ISerializable> interface is not supported.</span></span>  
  
12. <span data-ttu-id="1c569-119">不支援 Net.Tcp 和 PollingDuplex 繫結</span><span class="sxs-lookup"><span data-stu-id="1c569-119">Net.Tcp and PollingDuplex bindings are not supported</span></span>  
  
13. <span data-ttu-id="1c569-120">永遠使用 <xref:System.Runtime.Serialization.DataContractSerializer> 處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c569-120">The <xref:System.Runtime.Serialization.DataContractSerializer> will always be used for faults.</span></span>  
  
14. <span data-ttu-id="1c569-121">在可攜式子集專案中不支援 <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A>。</span><span class="sxs-lookup"><span data-stu-id="1c569-121"><xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is not supported in portable subset projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c569-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c569-122">See Also</span></span>  
 [<span data-ttu-id="1c569-123">使用 WCF 用戶端存取服務</span><span class="sxs-lookup"><span data-stu-id="1c569-123">Accessing Services Using a WCF Client</span></span>](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [<span data-ttu-id="1c569-124">可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="1c569-124">Portable Class Library</span></span>](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
