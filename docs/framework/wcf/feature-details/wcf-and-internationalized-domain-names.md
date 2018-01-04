---
title: "WCF 及國際化網域名稱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a0a6cd2a809648aadfba9bac2c4ab35c26b4c65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="b7c9e-102">WCF 及國際化網域名稱</span><span class="sxs-lookup"><span data-stu-id="b7c9e-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="b7c9e-103">已加入支援，以允許具有國際化網域名稱 (IDN) 的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="b7c9e-104">國際化網域名稱是包含非 ASCII 字元的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="b7c9e-105">這項支援包括兩種能力，即裝載具有 IDN 名稱之 WCF 服務，以及裝載對具有 IDN 名稱之 Web 服務進行交談的 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="b7c9e-106">System.Uri 和 IDN</span><span class="sxs-lookup"><span data-stu-id="b7c9e-106">System.Uri and IDN</span></span>  
 <span data-ttu-id="b7c9e-107"><xref:System.Uri> 有兩個屬性：<xref:System.Uri.Host%2A> 和 <xref:System.Uri.DnsSafeHost%2A>。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="b7c9e-108">這些屬性包含 Unicode 或 Punycode 值，因 IDN 組態設定而異。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="b7c9e-109">使用下列 XML 以在應用程式組態檔中啟用 IDN</span><span class="sxs-lookup"><span data-stu-id="b7c9e-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="b7c9e-110">\<Idn > 項目包含啟用的屬性，可以設定為下列值之一：</span><span class="sxs-lookup"><span data-stu-id="b7c9e-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1.  <span data-ttu-id="b7c9e-111">「 無 」</span><span class="sxs-lookup"><span data-stu-id="b7c9e-111">"None"</span></span>  
  
2.  <span data-ttu-id="b7c9e-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="b7c9e-112">"AllExceptIntranet"</span></span>  
  
3.  <span data-ttu-id="b7c9e-113">「 全部 」</span><span class="sxs-lookup"><span data-stu-id="b7c9e-113">"All"</span></span>  
  
 <span data-ttu-id="b7c9e-114">當 IDN 設定設為 [無] 時，Uri.Host 或 Uri.DnsSafeHost 並未不執行任何轉換。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="b7c9e-115">當 IDN 設定設為 「 全部 」 的 uri。主機會維持 Unicode 和 uri。DnsSafeHost 會轉換為 Punycode。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="b7c9e-116">當 IDN 設定設為"AllExceptIntranet"，uri。DnsSafeHost 網際網路位址轉換為 Punycode，對內部網路位址則保持為 Unicode。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="b7c9e-117">這個設定對正確解析 DNS 名稱很重要。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="b7c9e-118">請注意，Windows 8 和較新的版本不需要進行這個設定。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b7c9e-119">永遠不要使用 Punycode 將位址寫成硬式編碼。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="b7c9e-120">WCF 會根據您套用的組態設定來為您進行轉換。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b7c9e-121">將 Unicode 字元加入至 applicationHost.exe.config，請使用 UTF-8 編碼儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="b7c9e-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c9e-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7c9e-122">See Also</span></span>  
 [<span data-ttu-id="b7c9e-123">System.Uri</span><span class="sxs-lookup"><span data-stu-id="b7c9e-123">System.Uri</span></span>](http://msdn.microsoft.com/library/system.uri.aspx)
