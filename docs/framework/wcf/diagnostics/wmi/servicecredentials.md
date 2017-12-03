---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89aff21ed916e1b486a191f86dde5ed8b3e4ba22
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="e537e-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="e537e-102">ServiceCredentials</span></span>
<span data-ttu-id="e537e-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="e537e-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e537e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e537e-104">Syntax</span></span>  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e537e-105">方法</span><span class="sxs-lookup"><span data-stu-id="e537e-105">Methods</span></span>  
 <span data-ttu-id="e537e-106">ServiceCredentials 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="e537e-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e537e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e537e-107">Properties</span></span>  
 <span data-ttu-id="e537e-108">ServiceCredentials 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e537e-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="e537e-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="e537e-109">ClientCertificate</span></span>  
 <span data-ttu-id="e537e-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="e537e-110">Data type: string</span></span>  
  
 <span data-ttu-id="e537e-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e537e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e537e-112">用戶端憑證驗證與此服務的佈建設定。</span><span class="sxs-lookup"><span data-stu-id="e537e-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="e537e-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="e537e-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="e537e-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="e537e-114">Data type: string</span></span>  
  
 <span data-ttu-id="e537e-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e537e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e537e-116">這項服務目前發行的權杖驗證設定。</span><span class="sxs-lookup"><span data-stu-id="e537e-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="e537e-117">對等</span><span class="sxs-lookup"><span data-stu-id="e537e-117">Peer</span></span>  
 <span data-ttu-id="e537e-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="e537e-118">Data type: string</span></span>  
  
 <span data-ttu-id="e537e-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e537e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e537e-120">目前的認證驗證與對等傳輸端點將使用的佈建設定。</span><span class="sxs-lookup"><span data-stu-id="e537e-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="e537e-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="e537e-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="e537e-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="e537e-122">Data type: string</span></span>  
  
 <span data-ttu-id="e537e-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e537e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e537e-124">指定目前的安全對話設定。</span><span class="sxs-lookup"><span data-stu-id="e537e-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="e537e-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="e537e-125">ServiceCertificate</span></span>  
 <span data-ttu-id="e537e-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="e537e-126">Data type: string</span></span>  
  
 <span data-ttu-id="e537e-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e537e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e537e-128">與這項服務關聯的憑證。</span><span class="sxs-lookup"><span data-stu-id="e537e-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="e537e-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="e537e-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="e537e-130">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="e537e-130">Data type: string</span></span>  
  
 <span data-ttu-id="e537e-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e537e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e537e-132">這項服務的使用者名稱和密碼設定。</span><span class="sxs-lookup"><span data-stu-id="e537e-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="e537e-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="e537e-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="e537e-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="e537e-134">Data type: string</span></span>  
  
 <span data-ttu-id="e537e-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e537e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e537e-136">這項服務的 Windows 驗證設定。</span><span class="sxs-lookup"><span data-stu-id="e537e-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e537e-137">需求</span><span class="sxs-lookup"><span data-stu-id="e537e-137">Requirements</span></span>  
  
|<span data-ttu-id="e537e-138">MOF</span><span class="sxs-lookup"><span data-stu-id="e537e-138">MOF</span></span>|<span data-ttu-id="e537e-139">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="e537e-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e537e-140">命名空間</span><span class="sxs-lookup"><span data-stu-id="e537e-140">Namespace</span></span>|<span data-ttu-id="e537e-141">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="e537e-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e537e-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e537e-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
