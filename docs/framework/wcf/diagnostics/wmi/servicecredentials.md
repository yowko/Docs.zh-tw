---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d7e89acedc8fc1004b0198172e58813944df85f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262303"
---
# <a name="servicecredentials"></a><span data-ttu-id="c9984-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="c9984-102">ServiceCredentials</span></span>

<span data-ttu-id="c9984-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="c9984-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9984-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9984-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="c9984-105">方法</span><span class="sxs-lookup"><span data-stu-id="c9984-105">Methods</span></span>  

 <span data-ttu-id="c9984-106">ServiceCredentials 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="c9984-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c9984-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c9984-107">Properties</span></span>  

 <span data-ttu-id="c9984-108">ServiceCredentials 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="c9984-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="c9984-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="c9984-109">ClientCertificate</span></span>  

 <span data-ttu-id="c9984-110">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="c9984-110">Data type: string</span></span>  
  
 <span data-ttu-id="c9984-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9984-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9984-112">用戶端憑證驗證與此服務的佈建設定。</span><span class="sxs-lookup"><span data-stu-id="c9984-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="c9984-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="c9984-113">IssuedTokenAuthentication</span></span>  

 <span data-ttu-id="c9984-114">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="c9984-114">Data type: string</span></span>  
  
 <span data-ttu-id="c9984-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9984-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9984-116">這項服務目前發行的權杖驗證設定。</span><span class="sxs-lookup"><span data-stu-id="c9984-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="c9984-117">對等</span><span class="sxs-lookup"><span data-stu-id="c9984-117">Peer</span></span>  

 <span data-ttu-id="c9984-118">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="c9984-118">Data type: string</span></span>  
  
 <span data-ttu-id="c9984-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9984-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9984-120">目前的認證驗證與對等傳輸端點將使用的佈建設定。</span><span class="sxs-lookup"><span data-stu-id="c9984-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="c9984-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="c9984-121">SecureConversationAuthentication</span></span>  

 <span data-ttu-id="c9984-122">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="c9984-122">Data type: string</span></span>  
  
 <span data-ttu-id="c9984-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9984-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9984-124">指定目前的安全對話設定。</span><span class="sxs-lookup"><span data-stu-id="c9984-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="c9984-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="c9984-125">ServiceCertificate</span></span>  

 <span data-ttu-id="c9984-126">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="c9984-126">Data type: string</span></span>  
  
 <span data-ttu-id="c9984-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9984-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9984-128">與這項服務關聯的憑證。</span><span class="sxs-lookup"><span data-stu-id="c9984-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="c9984-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="c9984-129">UserNameAuthentication</span></span>  

 <span data-ttu-id="c9984-130">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="c9984-130">Data type: string</span></span>  
  
 <span data-ttu-id="c9984-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9984-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9984-132">這項服務的使用者名稱和密碼設定。</span><span class="sxs-lookup"><span data-stu-id="c9984-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="c9984-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="c9984-133">WindowsAuthentication</span></span>  

 <span data-ttu-id="c9984-134">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="c9984-134">Data type: string</span></span>  
  
 <span data-ttu-id="c9984-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9984-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9984-136">這項服務的 Windows 驗證設定。</span><span class="sxs-lookup"><span data-stu-id="c9984-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9984-137">規格需求</span><span class="sxs-lookup"><span data-stu-id="c9984-137">Requirements</span></span>  
  
|<span data-ttu-id="c9984-138">MOF</span><span class="sxs-lookup"><span data-stu-id="c9984-138">MOF</span></span>|<span data-ttu-id="c9984-139">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="c9984-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c9984-140">命名空間</span><span class="sxs-lookup"><span data-stu-id="c9984-140">Namespace</span></span>|<span data-ttu-id="c9984-141">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="c9984-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9984-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9984-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
