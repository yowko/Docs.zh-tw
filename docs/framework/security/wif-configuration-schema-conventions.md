---
title: WIF 組態結構描述慣例
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: dc2e8f7070af3ef907e4987964bb5aa83f889186
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070353"
---
# <a name="wif-configuration-schema-conventions"></a><span data-ttu-id="36448-102">WIF 組態結構描述慣例</span><span class="sxs-lookup"><span data-stu-id="36448-102">WIF Configuration Schema Conventions</span></span>
<span data-ttu-id="36448-103">本主題討論 Windows Identity Foundation (WIF) 組態主題中所使用的慣例，並描述 [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) 和 [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 區段中所使用的一些常見功能和屬性。</span><span class="sxs-lookup"><span data-stu-id="36448-103">This topic discusses conventions used throughout the Windows Identity Foundation (WIF) configuration topics and describes some common features and attributes used in the [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) and the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sections.</span></span>  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a><span data-ttu-id="36448-104">模式</span><span class="sxs-lookup"><span data-stu-id="36448-104">Modes</span></span>  
 <span data-ttu-id="36448-105">許多 WIF 組態元素都有 `mode` 屬性。</span><span class="sxs-lookup"><span data-stu-id="36448-105">Many of the WIF configuration elements have a `mode` attribute.</span></span> <span data-ttu-id="36448-106">這個屬性通常會控制哪一個類別用來執行處理的特定部分，以及哪一個組態元素允許作為目前元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="36448-106">This attribute typically controls which class is used to do a particular part of the processing and which configuration elements are allowed as child elements of the current element.</span></span> <span data-ttu-id="36448-107">如果組態檔中包含的項目會因模式設定而被忽略，將會引發組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="36448-107">A configuration error will be raised if elements that are included in the configuration file are ignored because of the mode settings.</span></span>  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a><span data-ttu-id="36448-108">TimeSpan 值</span><span class="sxs-lookup"><span data-stu-id="36448-108">Timespan Values</span></span>  
 <span data-ttu-id="36448-109">如果 <xref:System.TimeSpan> 作為屬性的類型，請檢閱 <xref:System.TimeSpan.Parse%28System.String%29> 方法以查看允許的格式。</span><span class="sxs-lookup"><span data-stu-id="36448-109">Where <xref:System.TimeSpan> is used as the type of an attribute, see the <xref:System.TimeSpan.Parse%28System.String%29> method to see the allowed format.</span></span> <span data-ttu-id="36448-110">此格式符合以下規格。</span><span class="sxs-lookup"><span data-stu-id="36448-110">This format conforms to the following specification.</span></span>  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 <span data-ttu-id="36448-111">例如，"30"、"30.00:00"、"30.00:00:00" 全都表示 30 天；"00:05"、"00:05:00"、"0.00:05:00.00" 全都表示 5 分鐘。</span><span class="sxs-lookup"><span data-stu-id="36448-111">For example, "30", "30.00:00", "30.00:00:00" all mean 30 days; and "00:05", "00:05:00", "0.00:05:00.00" all mean 5 minutes.</span></span>  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a><span data-ttu-id="36448-112">憑證參考</span><span class="sxs-lookup"><span data-stu-id="36448-112">Certificate References</span></span>  
 <span data-ttu-id="36448-113">數個項目會使用 `<certificateReference>` 元素來參考憑證。</span><span class="sxs-lookup"><span data-stu-id="36448-113">Several elements take references to certificates using the `<certificateReference>` element.</span></span> <span data-ttu-id="36448-114">參考憑證後，便可使用下列屬性。</span><span class="sxs-lookup"><span data-stu-id="36448-114">When referencing a certificate, the following attributes are available.</span></span>  
  
|||  
|-|-|  
|`storeLocation`|<span data-ttu-id="36448-115"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> 列舉值：`CurrentUser` 或 `CurrentMachine`。</span><span class="sxs-lookup"><span data-stu-id="36448-115">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreLocation> enumeration: `CurrentUser` or `CurrentMachine`.</span></span>|  
|`storeName`|<span data-ttu-id="36448-116"><xref:System.Security.Cryptography.X509Certificates.StoreName> 列舉值；此內容最有用的是 `My` 和 `TrustedPeople`。</span><span class="sxs-lookup"><span data-stu-id="36448-116">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreName> enumeration; the most useful for this context are `My` and `TrustedPeople`.</span></span>|  
|`x509FindType`|<span data-ttu-id="36448-117"><xref:System.Security.Cryptography.X509Certificates.X509FindType> 列舉值；此內容最有用的是 `FindBySubjectName` 和 `FindByThumbprint`。</span><span class="sxs-lookup"><span data-stu-id="36448-117">A value of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> enumeration; the most useful for this context are `FindBySubjectName` and `FindByThumbprint`.</span></span> <span data-ttu-id="36448-118">若要消除發生錯誤的機率，建議在生產環境中使用 `FindByThumbprint` 類型。</span><span class="sxs-lookup"><span data-stu-id="36448-118">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span>|  
|`findValue`|<span data-ttu-id="36448-119">用來根據 `x509FindType` 屬性尋找憑證的值。</span><span class="sxs-lookup"><span data-stu-id="36448-119">The value used to find the certificate, based on the `x509FindType` attribute.</span></span> <span data-ttu-id="36448-120">若要消除發生錯誤的機率，建議在生產環境中使用 `FindByThumbprint` 類型。</span><span class="sxs-lookup"><span data-stu-id="36448-120">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span> <span data-ttu-id="36448-121">指定 `FindByThumbPrint` 後，這個屬性接受的值是憑證指紋的十六進位字串格式；例如，"97249e1a5fa6bee5e515b82111ef524a4c91583f"。</span><span class="sxs-lookup"><span data-stu-id="36448-121">When `FindByThumbPrint` is specified, this attribute takes a value that is the hexadecimal-string form of the certificate thumbprint; for example, "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span></span>|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a><span data-ttu-id="36448-122">自訂類型參考</span><span class="sxs-lookup"><span data-stu-id="36448-122">Custom Type References</span></span>  
 <span data-ttu-id="36448-123">數個項目使用 `type` 屬性參考自訂類型。</span><span class="sxs-lookup"><span data-stu-id="36448-123">Several elements reference custom types using the `type` attribute.</span></span> <span data-ttu-id="36448-124">這個屬性應該指定自訂類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="36448-124">This attribute should specify the name of the custom type.</span></span> <span data-ttu-id="36448-125">若要從全域組件快取 (GAC) 中參考類型，應該使用強式名稱。</span><span class="sxs-lookup"><span data-stu-id="36448-125">To reference a type from the Global Assembly Cache (GAC), a strong name should be used.</span></span> <span data-ttu-id="36448-126">若要從 Bin/ 目錄中的組件參考類型，可能會使用簡單的組件限定參考。</span><span class="sxs-lookup"><span data-stu-id="36448-126">To reference a type from an assembly in the Bin/ directory, a simple assembly-qualified reference may be used.</span></span> <span data-ttu-id="36448-127">定義在 App_Code/ 目錄中的類型，也可透過簡單指定不含合格組件的類型名稱來參考。</span><span class="sxs-lookup"><span data-stu-id="36448-127">Types defined in the App_Code/ directory may also be referenced by simply specifying the type name with no qualifying assembly.</span></span>  
  
 <span data-ttu-id="36448-128">自訂類型必須衍生自指定的類型，而且必須提供 `public` 預設 (0 個引數) 建構函式。</span><span class="sxs-lookup"><span data-stu-id="36448-128">Custom types must be derived from the type specified and they must provide a `public` default (0 argument) constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36448-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36448-129">See Also</span></span>  
 [<span data-ttu-id="36448-130">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="36448-130">\<system.identityModel></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [<span data-ttu-id="36448-131">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="36448-131">\<system.identityModel.services></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
