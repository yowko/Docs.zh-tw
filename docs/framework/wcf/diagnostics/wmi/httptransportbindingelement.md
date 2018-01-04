---
title: HttpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6370284dbd9c680b29f315c791ea76356e7b36f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="09956-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="09956-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="09956-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="09956-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09956-104">語法</span><span class="sxs-lookup"><span data-stu-id="09956-104">Syntax</span></span>  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="09956-105">方法</span><span class="sxs-lookup"><span data-stu-id="09956-105">Methods</span></span>  
 <span data-ttu-id="09956-106">HttpTransportBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="09956-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="09956-107">屬性</span><span class="sxs-lookup"><span data-stu-id="09956-107">Properties</span></span>  
 <span data-ttu-id="09956-108">HttpTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="09956-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="09956-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="09956-109">AllowCookies</span></span>  
 <span data-ttu-id="09956-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="09956-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="09956-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-112">表示用戶端是否接受 Cookie 並在未來的要求傳播 Cookie 的值。</span><span class="sxs-lookup"><span data-stu-id="09956-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="09956-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="09956-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="09956-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="09956-114">Data type: string</span></span>  
  
 <span data-ttu-id="09956-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-116">用於驗證由 HTTP 接聽項處理之用戶端要求的驗證配置。</span><span class="sxs-lookup"><span data-stu-id="09956-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="09956-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="09956-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="09956-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="09956-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="09956-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-120">代表是否針對本機位址略過 Proxy 的值。</span><span class="sxs-lookup"><span data-stu-id="09956-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="09956-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="09956-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="09956-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="09956-122">Data type: string</span></span>  
  
 <span data-ttu-id="09956-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-124">代表主機名稱是否用於連線到服務的值 (當符合 URI 時)。</span><span class="sxs-lookup"><span data-stu-id="09956-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="09956-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="09956-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="09956-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="09956-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="09956-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-128">啟用時，不論活動等級為何，HTTP 連線會維持開啟。</span><span class="sxs-lookup"><span data-stu-id="09956-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="09956-129">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="09956-129">MaxBufferSize</span></span>  
 <span data-ttu-id="09956-130">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="09956-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="09956-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-132">緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="09956-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="09956-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="09956-133">ProxyAddress</span></span>  
 <span data-ttu-id="09956-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="09956-134">Data type: string</span></span>  
  
 <span data-ttu-id="09956-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-136">包含用於 HTTP 要求之 Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="09956-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="09956-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="09956-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="09956-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="09956-138">Data type: string</span></span>  
  
 <span data-ttu-id="09956-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-140">用於驗證由 HTTP Proxy 處理之用戶端要求的驗證配置。</span><span class="sxs-lookup"><span data-stu-id="09956-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="09956-141">Realm</span><span class="sxs-lookup"><span data-stu-id="09956-141">Realm</span></span>  
 <span data-ttu-id="09956-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="09956-142">Data type: string</span></span>  
  
 <span data-ttu-id="09956-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-144">驗證領域。</span><span class="sxs-lookup"><span data-stu-id="09956-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="09956-145">TransferMode</span><span class="sxs-lookup"><span data-stu-id="09956-145">TransferMode</span></span>  
 <span data-ttu-id="09956-146">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="09956-146">Data type: string</span></span>  
  
 <span data-ttu-id="09956-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-148">代表訊息是經過緩衝處理或資料流處理，或為要求或回應的值。</span><span class="sxs-lookup"><span data-stu-id="09956-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="09956-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="09956-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="09956-150">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="09956-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="09956-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-152">代表是否已在伺服器啟用「不安全的連線共用」的值。</span><span class="sxs-lookup"><span data-stu-id="09956-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="09956-153">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="09956-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="09956-154">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="09956-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="09956-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="09956-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09956-156">代表是否使用全機器追蹤 Proxy 設定，而非使用者特定設定的值。</span><span class="sxs-lookup"><span data-stu-id="09956-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09956-157">需求</span><span class="sxs-lookup"><span data-stu-id="09956-157">Requirements</span></span>  
  
|<span data-ttu-id="09956-158">MOF</span><span class="sxs-lookup"><span data-stu-id="09956-158">MOF</span></span>|<span data-ttu-id="09956-159">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="09956-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="09956-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="09956-160">Namespace</span></span>|<span data-ttu-id="09956-161">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="09956-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09956-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="09956-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
