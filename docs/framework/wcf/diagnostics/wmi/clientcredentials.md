---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: aa852ff82c44a3b5009dbc70e1067face44cbbe9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486372"
---
# <a name="clientcredentials"></a><span data-ttu-id="a1492-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="a1492-102">ClientCredentials</span></span>
<span data-ttu-id="a1492-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="a1492-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1492-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1492-104">Syntax</span></span>  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a1492-105">方法</span><span class="sxs-lookup"><span data-stu-id="a1492-105">Methods</span></span>  
 <span data-ttu-id="a1492-106">ClientCredentials 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="a1492-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a1492-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a1492-107">Properties</span></span>  
 <span data-ttu-id="a1492-108">ClientCredentials 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a1492-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="a1492-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="a1492-109">ClientCertificate</span></span>  
 <span data-ttu-id="a1492-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1492-110">Data type: string</span></span>  
  
 <span data-ttu-id="a1492-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1492-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1492-112">用戶端用來向服務驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a1492-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="a1492-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="a1492-113">HttpDigest</span></span>  
 <span data-ttu-id="a1492-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1492-114">Data type: string</span></span>  
  
 <span data-ttu-id="a1492-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1492-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1492-116">目前的 Http 摘要式認證。</span><span class="sxs-lookup"><span data-stu-id="a1492-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="a1492-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="a1492-117">IssuedToken</span></span>  
 <span data-ttu-id="a1492-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1492-118">Data type: string</span></span>  
  
 <span data-ttu-id="a1492-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1492-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1492-120">用來聯繫本機安全性權杖服務的端點位址與繫結。</span><span class="sxs-lookup"><span data-stu-id="a1492-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="a1492-121">對等</span><span class="sxs-lookup"><span data-stu-id="a1492-121">Peer</span></span>  
 <span data-ttu-id="a1492-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1492-122">Data type: string</span></span>  
  
 <span data-ttu-id="a1492-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1492-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1492-124">對等節點用來向 mesh 中的其他節點驗證自己時使用的認證。</span><span class="sxs-lookup"><span data-stu-id="a1492-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="a1492-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="a1492-125">ServiceCertificate</span></span>  
 <span data-ttu-id="a1492-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1492-126">Data type: string</span></span>  
  
 <span data-ttu-id="a1492-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1492-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1492-128">服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a1492-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="a1492-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="a1492-129">SupportInteractive</span></span>  
 <span data-ttu-id="a1492-130">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="a1492-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1492-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1492-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1492-132">指定認證是否支援互動式交涉的布林值。</span><span class="sxs-lookup"><span data-stu-id="a1492-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="a1492-133">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="a1492-133">UserName</span></span>  
 <span data-ttu-id="a1492-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1492-134">Data type: string</span></span>  
  
 <span data-ttu-id="a1492-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1492-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1492-136">用戶端用來向服務驗證自身的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a1492-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="a1492-137">Windows</span><span class="sxs-lookup"><span data-stu-id="a1492-137">Windows</span></span>  
 <span data-ttu-id="a1492-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a1492-138">Data type: string</span></span>  
  
 <span data-ttu-id="a1492-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a1492-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1492-140">用戶端用來向服務驗證自身的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="a1492-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1492-141">需求</span><span class="sxs-lookup"><span data-stu-id="a1492-141">Requirements</span></span>  
  
|<span data-ttu-id="a1492-142">MOF</span><span class="sxs-lookup"><span data-stu-id="a1492-142">MOF</span></span>|<span data-ttu-id="a1492-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="a1492-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a1492-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="a1492-144">Namespace</span></span>|<span data-ttu-id="a1492-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="a1492-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1492-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1492-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
