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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b1542406caf9bb3684ccf2d97ed441f1dc3d0db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="32133-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="32133-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="32133-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="32133-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32133-104">語法</span><span class="sxs-lookup"><span data-stu-id="32133-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="32133-105">方法</span><span class="sxs-lookup"><span data-stu-id="32133-105">Methods</span></span>  
 <span data-ttu-id="32133-106">HttpTransportBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="32133-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="32133-107">屬性</span><span class="sxs-lookup"><span data-stu-id="32133-107">Properties</span></span>  
 <span data-ttu-id="32133-108">HttpTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="32133-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="32133-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="32133-109">AllowCookies</span></span>  
 <span data-ttu-id="32133-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="32133-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="32133-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-112">表示用戶端是否接受 Cookie 並在未來的要求傳播 Cookie 的值。</span><span class="sxs-lookup"><span data-stu-id="32133-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="32133-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="32133-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="32133-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="32133-114">Data type: string</span></span>  
  
 <span data-ttu-id="32133-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-116">用於驗證由 HTTP 接聽項處理之用戶端要求的驗證配置。</span><span class="sxs-lookup"><span data-stu-id="32133-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="32133-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="32133-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="32133-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="32133-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="32133-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-120">代表是否針對本機位址略過 Proxy 的值。</span><span class="sxs-lookup"><span data-stu-id="32133-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="32133-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="32133-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="32133-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="32133-122">Data type: string</span></span>  
  
 <span data-ttu-id="32133-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-124">代表主機名稱是否用於連線到服務的值 (當符合 URI 時)。</span><span class="sxs-lookup"><span data-stu-id="32133-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="32133-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="32133-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="32133-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="32133-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="32133-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-128">啟用時，不論活動等級為何，HTTP 連線會維持開啟。</span><span class="sxs-lookup"><span data-stu-id="32133-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="32133-129">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="32133-129">MaxBufferSize</span></span>  
 <span data-ttu-id="32133-130">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="32133-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="32133-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-132">緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="32133-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="32133-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="32133-133">ProxyAddress</span></span>  
 <span data-ttu-id="32133-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="32133-134">Data type: string</span></span>  
  
 <span data-ttu-id="32133-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-136">包含用於 HTTP 要求之 Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="32133-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="32133-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="32133-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="32133-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="32133-138">Data type: string</span></span>  
  
 <span data-ttu-id="32133-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-140">用於驗證由 HTTP Proxy 處理之用戶端要求的驗證配置。</span><span class="sxs-lookup"><span data-stu-id="32133-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="32133-141">Realm</span><span class="sxs-lookup"><span data-stu-id="32133-141">Realm</span></span>  
 <span data-ttu-id="32133-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="32133-142">Data type: string</span></span>  
  
 <span data-ttu-id="32133-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-144">驗證領域。</span><span class="sxs-lookup"><span data-stu-id="32133-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="32133-145">TransferMode</span><span class="sxs-lookup"><span data-stu-id="32133-145">TransferMode</span></span>  
 <span data-ttu-id="32133-146">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="32133-146">Data type: string</span></span>  
  
 <span data-ttu-id="32133-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-148">代表訊息是經過緩衝處理或資料流處理，或為要求或回應的值。</span><span class="sxs-lookup"><span data-stu-id="32133-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="32133-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="32133-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="32133-150">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="32133-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="32133-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-152">代表是否已在伺服器啟用「不安全的連線共用」的值。</span><span class="sxs-lookup"><span data-stu-id="32133-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="32133-153">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="32133-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="32133-154">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="32133-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="32133-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="32133-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32133-156">代表是否使用全機器追蹤 Proxy 設定，而非使用者特定設定的值。</span><span class="sxs-lookup"><span data-stu-id="32133-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32133-157">需求</span><span class="sxs-lookup"><span data-stu-id="32133-157">Requirements</span></span>  
  
|<span data-ttu-id="32133-158">MOF</span><span class="sxs-lookup"><span data-stu-id="32133-158">MOF</span></span>|<span data-ttu-id="32133-159">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="32133-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="32133-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="32133-160">Namespace</span></span>|<span data-ttu-id="32133-161">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="32133-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32133-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32133-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
