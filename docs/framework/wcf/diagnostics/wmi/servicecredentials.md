---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 18100ac36b5116c2373171ff795fc23b75bbd6f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572116"
---
# <a name="servicecredentials"></a><span data-ttu-id="aed3f-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="aed3f-102">ServiceCredentials</span></span>
<span data-ttu-id="aed3f-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="aed3f-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aed3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="aed3f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="aed3f-105">方法</span><span class="sxs-lookup"><span data-stu-id="aed3f-105">Methods</span></span>  
 <span data-ttu-id="aed3f-106">ServiceCredentials 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="aed3f-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aed3f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="aed3f-107">Properties</span></span>  
 <span data-ttu-id="aed3f-108">ServiceCredentials 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="aed3f-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="aed3f-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="aed3f-109">ClientCertificate</span></span>  
 <span data-ttu-id="aed3f-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="aed3f-110">Data type: string</span></span>  
  
 <span data-ttu-id="aed3f-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="aed3f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aed3f-112">用戶端憑證驗證與此服務的佈建設定。</span><span class="sxs-lookup"><span data-stu-id="aed3f-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="aed3f-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="aed3f-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="aed3f-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="aed3f-114">Data type: string</span></span>  
  
 <span data-ttu-id="aed3f-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="aed3f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aed3f-116">這項服務目前發行的權杖驗證設定。</span><span class="sxs-lookup"><span data-stu-id="aed3f-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="aed3f-117">對等</span><span class="sxs-lookup"><span data-stu-id="aed3f-117">Peer</span></span>  
 <span data-ttu-id="aed3f-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="aed3f-118">Data type: string</span></span>  
  
 <span data-ttu-id="aed3f-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="aed3f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aed3f-120">目前的認證驗證與對等傳輸端點將使用的佈建設定。</span><span class="sxs-lookup"><span data-stu-id="aed3f-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="aed3f-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="aed3f-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="aed3f-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="aed3f-122">Data type: string</span></span>  
  
 <span data-ttu-id="aed3f-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="aed3f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aed3f-124">指定目前的安全對話設定。</span><span class="sxs-lookup"><span data-stu-id="aed3f-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="aed3f-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="aed3f-125">ServiceCertificate</span></span>  
 <span data-ttu-id="aed3f-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="aed3f-126">Data type: string</span></span>  
  
 <span data-ttu-id="aed3f-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="aed3f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aed3f-128">與這項服務關聯的憑證。</span><span class="sxs-lookup"><span data-stu-id="aed3f-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="aed3f-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="aed3f-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="aed3f-130">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="aed3f-130">Data type: string</span></span>  
  
 <span data-ttu-id="aed3f-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="aed3f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aed3f-132">這項服務的使用者名稱和密碼設定。</span><span class="sxs-lookup"><span data-stu-id="aed3f-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="aed3f-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="aed3f-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="aed3f-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="aed3f-134">Data type: string</span></span>  
  
 <span data-ttu-id="aed3f-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="aed3f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aed3f-136">這項服務的 Windows 驗證設定。</span><span class="sxs-lookup"><span data-stu-id="aed3f-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aed3f-137">需求</span><span class="sxs-lookup"><span data-stu-id="aed3f-137">Requirements</span></span>  
  
|<span data-ttu-id="aed3f-138">MOF</span><span class="sxs-lookup"><span data-stu-id="aed3f-138">MOF</span></span>|<span data-ttu-id="aed3f-139">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="aed3f-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="aed3f-140">命名空間</span><span class="sxs-lookup"><span data-stu-id="aed3f-140">Namespace</span></span>|<span data-ttu-id="aed3f-141">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="aed3f-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aed3f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aed3f-142">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceCredentials>
