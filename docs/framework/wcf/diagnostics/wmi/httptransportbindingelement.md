---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 34ad4b8534d082d7f5248d42d70ca5bd0647a5dc
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454313"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="6d016-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6d016-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="6d016-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6d016-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d016-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d016-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="6d016-105">方法</span><span class="sxs-lookup"><span data-stu-id="6d016-105">Methods</span></span>  
 <span data-ttu-id="6d016-106">HttpTransportBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="6d016-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6d016-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6d016-107">Properties</span></span>  
 <span data-ttu-id="6d016-108">HttpTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6d016-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="6d016-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="6d016-109">AllowCookies</span></span>  
 <span data-ttu-id="6d016-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="6d016-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="6d016-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-112">表示用戶端是否接受 Cookie 並在未來的要求傳播 Cookie 的值。</span><span class="sxs-lookup"><span data-stu-id="6d016-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="6d016-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="6d016-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="6d016-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6d016-114">Data type: string</span></span>  
  
 <span data-ttu-id="6d016-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-116">用於驗證由 HTTP 接聽項處理之用戶端要求的驗證配置。</span><span class="sxs-lookup"><span data-stu-id="6d016-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="6d016-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="6d016-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="6d016-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="6d016-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6d016-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-120">代表是否針對本機位址略過 Proxy 的值。</span><span class="sxs-lookup"><span data-stu-id="6d016-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="6d016-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="6d016-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="6d016-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6d016-122">Data type: string</span></span>  
  
 <span data-ttu-id="6d016-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-124">代表主機名稱是否用於連線到服務的值 (當符合 URI 時)。</span><span class="sxs-lookup"><span data-stu-id="6d016-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="6d016-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="6d016-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="6d016-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="6d016-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="6d016-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-128">啟用時，不論活動等級為何，HTTP 連線會維持開啟。</span><span class="sxs-lookup"><span data-stu-id="6d016-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="6d016-129">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="6d016-129">MaxBufferSize</span></span>  
 <span data-ttu-id="6d016-130">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="6d016-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="6d016-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-132">緩衝集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="6d016-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="6d016-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="6d016-133">ProxyAddress</span></span>  
 <span data-ttu-id="6d016-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6d016-134">Data type: string</span></span>  
  
 <span data-ttu-id="6d016-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-136">包含用於 HTTP 要求之 Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="6d016-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="6d016-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="6d016-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="6d016-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6d016-138">Data type: string</span></span>  
  
 <span data-ttu-id="6d016-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-140">用於驗證由 HTTP Proxy 處理之用戶端要求的驗證配置。</span><span class="sxs-lookup"><span data-stu-id="6d016-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="6d016-141">Realm</span><span class="sxs-lookup"><span data-stu-id="6d016-141">Realm</span></span>  
 <span data-ttu-id="6d016-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6d016-142">Data type: string</span></span>  
  
 <span data-ttu-id="6d016-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-144">驗證領域。</span><span class="sxs-lookup"><span data-stu-id="6d016-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="6d016-145">TransferMode</span><span class="sxs-lookup"><span data-stu-id="6d016-145">TransferMode</span></span>  
 <span data-ttu-id="6d016-146">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6d016-146">Data type: string</span></span>  
  
 <span data-ttu-id="6d016-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-148">代表訊息是經過緩衝處理或資料流處理，或為要求或回應的值。</span><span class="sxs-lookup"><span data-stu-id="6d016-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="6d016-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="6d016-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="6d016-150">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="6d016-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="6d016-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-152">代表是否已在伺服器啟用「不安全的連線共用」的值。</span><span class="sxs-lookup"><span data-stu-id="6d016-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="6d016-153">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="6d016-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="6d016-154">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="6d016-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="6d016-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6d016-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d016-156">代表是否使用全機器追蹤 Proxy 設定，而非使用者特定設定的值。</span><span class="sxs-lookup"><span data-stu-id="6d016-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d016-157">需求</span><span class="sxs-lookup"><span data-stu-id="6d016-157">Requirements</span></span>  
  
|<span data-ttu-id="6d016-158">MOF</span><span class="sxs-lookup"><span data-stu-id="6d016-158">MOF</span></span>|<span data-ttu-id="6d016-159">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="6d016-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6d016-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="6d016-160">Namespace</span></span>|<span data-ttu-id="6d016-161">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="6d016-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d016-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d016-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
