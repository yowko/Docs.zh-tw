---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
author: BrucePerlerMS
ms.openlocfilehash: c79eb11fcc1973a3ef25a78afb8b141443d865c3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47398861"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="5a6a9-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="5a6a9-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="5a6a9-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="5a6a9-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a6a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a6a9-104">Syntax</span></span>  
  
```  
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5a6a9-105">方法</span><span class="sxs-lookup"><span data-stu-id="5a6a9-105">Methods</span></span>  
 <span data-ttu-id="5a6a9-106">LocalServiceSecuritySettings 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5a6a9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5a6a9-107">Properties</span></span>  
 <span data-ttu-id="5a6a9-108">LocalServiceSecuritySettings 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5a6a9-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="5a6a9-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="5a6a9-109">DetectReplays</span></span>  
 <span data-ttu-id="5a6a9-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="5a6a9-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="5a6a9-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-112">布林值，這個值會指定是否會偵測及自動處理對通道所發出的重新執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="5a6a9-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="5a6a9-113">InactivityTimeout</span></span>  
 <span data-ttu-id="5a6a9-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="5a6a9-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="5a6a9-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-116">服務支援的暫止安全性工作階段數目上限。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="5a6a9-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="5a6a9-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="5a6a9-118">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="5a6a9-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="5a6a9-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-120">TimeSpan 指定發出給所有新的安全性 Cookie 的存留期。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="5a6a9-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="5a6a9-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="5a6a9-122">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="5a6a9-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="5a6a9-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-124">可以快取的 Cookie 數目上限。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="5a6a9-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="5a6a9-125">MaxClockSkew</span></span>  
 <span data-ttu-id="5a6a9-126">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="5a6a9-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="5a6a9-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-128">TimeSpan 指定通訊雙方之系統時鐘之間的最大時間差異。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="5a6a9-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="5a6a9-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="5a6a9-130">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="5a6a9-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="5a6a9-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-132">服務上的最大暫止連線數目。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="5a6a9-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="5a6a9-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="5a6a9-134">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="5a6a9-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="5a6a9-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-136">可以同時為作用中的安全性交涉數目。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="5a6a9-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="5a6a9-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="5a6a9-138">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="5a6a9-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="5a6a9-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-140">TimeSpan 指定伺服器和用戶端之間安全性交涉階段的最大持續期間。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="5a6a9-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="5a6a9-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="5a6a9-142">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="5a6a9-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="5a6a9-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-144">布林值，指定使用 WS-Reliable 訊息的連線是否會在傳輸失敗之後嘗試重新連線。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="5a6a9-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="5a6a9-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="5a6a9-146">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="5a6a9-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="5a6a9-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-148">用於偵測重新執行的已快取 Nonce 數目。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="5a6a9-149">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="5a6a9-149">ReplayWindow</span></span>  
 <span data-ttu-id="5a6a9-150">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="5a6a9-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="5a6a9-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-152">TimeSpan 指定個別訊息 Nonce 有效的持續期間。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="5a6a9-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="5a6a9-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="5a6a9-154">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="5a6a9-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="5a6a9-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-156">指定持續期間的 TimeSpan，啟動器將在這段期間過後更新安全性工作階段的金鑰。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="5a6a9-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="5a6a9-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="5a6a9-158">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="5a6a9-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="5a6a9-159">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-160">TimeSpan，指定前一個工作階段金鑰在金鑰更新期間對傳入訊息屬有效的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="5a6a9-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="5a6a9-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="5a6a9-162">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="5a6a9-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="5a6a9-163">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5a6a9-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a6a9-164">TimeSpan，指定時間戳記有效的持續期間。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a6a9-165">需求</span><span class="sxs-lookup"><span data-stu-id="5a6a9-165">Requirements</span></span>  
  
|<span data-ttu-id="5a6a9-166">MOF</span><span class="sxs-lookup"><span data-stu-id="5a6a9-166">MOF</span></span>|<span data-ttu-id="5a6a9-167">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="5a6a9-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5a6a9-168">命名空間</span><span class="sxs-lookup"><span data-stu-id="5a6a9-168">Namespace</span></span>|<span data-ttu-id="5a6a9-169">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="5a6a9-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a6a9-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a6a9-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
