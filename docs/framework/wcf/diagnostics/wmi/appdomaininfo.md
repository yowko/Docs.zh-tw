---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76fee9673514287dd120a215fc843e4d995e68c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="7178c-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="7178c-102">AppDomainInfo</span></span>
<span data-ttu-id="7178c-103">應用程式定義域資訊</span><span class="sxs-lookup"><span data-stu-id="7178c-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7178c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7178c-104">Syntax</span></span>  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7178c-105">方法</span><span class="sxs-lookup"><span data-stu-id="7178c-105">Methods</span></span>  
 <span data-ttu-id="7178c-106">AppDomainInfo 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="7178c-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7178c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="7178c-107">Properties</span></span>  
 <span data-ttu-id="7178c-108">AppDomainInfo 類別具有以下屬性：</span><span class="sxs-lookup"><span data-stu-id="7178c-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="7178c-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="7178c-109">AppDomainId</span></span>  
 <span data-ttu-id="7178c-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="7178c-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="7178c-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7178c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7178c-112">appdomain 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7178c-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="7178c-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="7178c-113">IsDefault</span></span>  
 <span data-ttu-id="7178c-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="7178c-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="7178c-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7178c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7178c-116">指出 appdomain 是否為預設的 appdomain。</span><span class="sxs-lookup"><span data-stu-id="7178c-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="7178c-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="7178c-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="7178c-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="7178c-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="7178c-119">存取類型：讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="7178c-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="7178c-120">值，指定是否記錄了格式錯誤的訊息。</span><span class="sxs-lookup"><span data-stu-id="7178c-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="7178c-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="7178c-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="7178c-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="7178c-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="7178c-123">存取類型：讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="7178c-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="7178c-124">值，指定是否在服務層級追蹤訊息 (在加密和傳輸相關轉換之前)。</span><span class="sxs-lookup"><span data-stu-id="7178c-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="7178c-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="7178c-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="7178c-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="7178c-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="7178c-127">存取類型：讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="7178c-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="7178c-128">值，指定是否在傳輸層級追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="7178c-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="7178c-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="7178c-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="7178c-130">資料型別：TraceListener 陣列</span><span class="sxs-lookup"><span data-stu-id="7178c-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="7178c-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7178c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7178c-132">接聽 System.Wmi.MessageLogging 追蹤來源的集合追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="7178c-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="7178c-133">名稱</span><span class="sxs-lookup"><span data-stu-id="7178c-133">Name</span></span>  
 <span data-ttu-id="7178c-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="7178c-134">Data type: string</span></span>  
  
 <span data-ttu-id="7178c-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7178c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7178c-136">appdomain 的名稱。</span><span class="sxs-lookup"><span data-stu-id="7178c-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="7178c-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="7178c-137">PerformanceCounters</span></span>  
 <span data-ttu-id="7178c-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="7178c-138">Data type: string</span></span>  
  
 <span data-ttu-id="7178c-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7178c-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7178c-140">appdomain 中作用中效能計數器的範圍。</span><span class="sxs-lookup"><span data-stu-id="7178c-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="7178c-141">ProcessId</span><span class="sxs-lookup"><span data-stu-id="7178c-141">ProcessId</span></span>  
 <span data-ttu-id="7178c-142">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="7178c-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="7178c-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7178c-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7178c-144">處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="7178c-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="7178c-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="7178c-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="7178c-146">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="7178c-146">Data type: string</span></span>  
  
 <span data-ttu-id="7178c-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7178c-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7178c-148">服務組態的路徑。</span><span class="sxs-lookup"><span data-stu-id="7178c-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="7178c-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="7178c-149">TraceLevel</span></span>  
 <span data-ttu-id="7178c-150">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="7178c-150">Data type: string</span></span>  
  
 <span data-ttu-id="7178c-151">存取類型：讀取/寫入</span><span class="sxs-lookup"><span data-stu-id="7178c-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="7178c-152">System.Wmi 追蹤來源的追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="7178c-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="7178c-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="7178c-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="7178c-154">資料型別：TraceListener 陣列</span><span class="sxs-lookup"><span data-stu-id="7178c-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="7178c-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7178c-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7178c-156">來自 System.ServiceModel 追蹤來源的接聽項集合。</span><span class="sxs-lookup"><span data-stu-id="7178c-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7178c-157">需求</span><span class="sxs-lookup"><span data-stu-id="7178c-157">Requirements</span></span>  
  
|<span data-ttu-id="7178c-158">MOF</span><span class="sxs-lookup"><span data-stu-id="7178c-158">MOF</span></span>|<span data-ttu-id="7178c-159">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="7178c-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7178c-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="7178c-160">Namespace</span></span>|<span data-ttu-id="7178c-161">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="7178c-161">Defined in root\ServiceModel</span></span>|
