---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: bf906e09ae71d26f8e95877f1c545c0724d57b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485734"
---
# <a name="servicecredentials"></a><span data-ttu-id="843db-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="843db-102">ServiceCredentials</span></span>
<span data-ttu-id="843db-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="843db-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="843db-104">語法</span><span class="sxs-lookup"><span data-stu-id="843db-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="843db-105">方法</span><span class="sxs-lookup"><span data-stu-id="843db-105">Methods</span></span>  
 <span data-ttu-id="843db-106">ServiceCredentials 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="843db-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="843db-107">屬性</span><span class="sxs-lookup"><span data-stu-id="843db-107">Properties</span></span>  
 <span data-ttu-id="843db-108">ServiceCredentials 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="843db-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="843db-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="843db-109">ClientCertificate</span></span>  
 <span data-ttu-id="843db-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="843db-110">Data type: string</span></span>  
  
 <span data-ttu-id="843db-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="843db-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843db-112">用戶端憑證驗證與此服務的佈建設定。</span><span class="sxs-lookup"><span data-stu-id="843db-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="843db-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="843db-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="843db-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="843db-114">Data type: string</span></span>  
  
 <span data-ttu-id="843db-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="843db-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843db-116">這項服務目前發行的權杖驗證設定。</span><span class="sxs-lookup"><span data-stu-id="843db-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="843db-117">對等</span><span class="sxs-lookup"><span data-stu-id="843db-117">Peer</span></span>  
 <span data-ttu-id="843db-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="843db-118">Data type: string</span></span>  
  
 <span data-ttu-id="843db-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="843db-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843db-120">目前的認證驗證與對等傳輸端點將使用的佈建設定。</span><span class="sxs-lookup"><span data-stu-id="843db-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="843db-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="843db-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="843db-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="843db-122">Data type: string</span></span>  
  
 <span data-ttu-id="843db-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="843db-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843db-124">指定目前的安全對話設定。</span><span class="sxs-lookup"><span data-stu-id="843db-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="843db-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="843db-125">ServiceCertificate</span></span>  
 <span data-ttu-id="843db-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="843db-126">Data type: string</span></span>  
  
 <span data-ttu-id="843db-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="843db-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843db-128">與這項服務關聯的憑證。</span><span class="sxs-lookup"><span data-stu-id="843db-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="843db-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="843db-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="843db-130">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="843db-130">Data type: string</span></span>  
  
 <span data-ttu-id="843db-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="843db-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843db-132">這項服務的使用者名稱和密碼設定。</span><span class="sxs-lookup"><span data-stu-id="843db-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="843db-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="843db-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="843db-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="843db-134">Data type: string</span></span>  
  
 <span data-ttu-id="843db-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="843db-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843db-136">這項服務的 Windows 驗證設定。</span><span class="sxs-lookup"><span data-stu-id="843db-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="843db-137">需求</span><span class="sxs-lookup"><span data-stu-id="843db-137">Requirements</span></span>  
  
|<span data-ttu-id="843db-138">MOF</span><span class="sxs-lookup"><span data-stu-id="843db-138">MOF</span></span>|<span data-ttu-id="843db-139">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="843db-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="843db-140">命名空間</span><span class="sxs-lookup"><span data-stu-id="843db-140">Namespace</span></span>|<span data-ttu-id="843db-141">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="843db-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="843db-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="843db-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
