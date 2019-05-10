---
title: HOW TO：在 WSFederationHttpBinding 上停用安全工作階段
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 73a51bd477a434b48f91406d08762fe886676b90
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626875"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="681d2-102">HOW TO：在 WSFederationHttpBinding 上停用安全工作階段</span><span class="sxs-lookup"><span data-stu-id="681d2-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>
<span data-ttu-id="681d2-103">某些服務可能會要求聯合認證，但卻不支援安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="681d2-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="681d2-104">在此情況下，您必須停用安全工作階段功能。</span><span class="sxs-lookup"><span data-stu-id="681d2-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="681d2-105">與 <xref:System.ServiceModel.WSHttpBinding> 不同的是，<xref:System.ServiceModel.WSFederationHttpBinding> 類別不會在您與服務進行通訊時，提供停用安全工作階段的方法。</span><span class="sxs-lookup"><span data-stu-id="681d2-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="681d2-106">反之，您必須建立自訂繫結，以便使用啟動安裝程式繫結來取代安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="681d2-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>  
  
 <span data-ttu-id="681d2-107">此主題將示範如何修改 <xref:System.ServiceModel.WSFederationHttpBinding> 內所包含的繫結項目來建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="681d2-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="681d2-108">除了不使用安全工作階段之外，其餘結果會與 <xref:System.ServiceModel.WSFederationHttpBinding> 相同。</span><span class="sxs-lookup"><span data-stu-id="681d2-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="681d2-109">若要建立一個不包含安全工作階段的自訂聯合繫結</span><span class="sxs-lookup"><span data-stu-id="681d2-109">To create a custom federated binding without secure session</span></span>  
  
1. <span data-ttu-id="681d2-110">在程式碼中以命令方式建立 <xref:System.ServiceModel.WSFederationHttpBinding> 類別的執行個體，或是從組態檔中載入一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="681d2-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>  
  
2. <span data-ttu-id="681d2-111">將 <xref:System.ServiceModel.WSFederationHttpBinding> 複製到 <xref:System.ServiceModel.Channels.CustomBinding>。</span><span class="sxs-lookup"><span data-stu-id="681d2-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
3. <span data-ttu-id="681d2-112">在 <xref:System.ServiceModel.Channels.SecurityBindingElement> 中尋找 <xref:System.ServiceModel.Channels.CustomBinding>。</span><span class="sxs-lookup"><span data-stu-id="681d2-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
4. <span data-ttu-id="681d2-113">在 <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> 中尋找 <xref:System.ServiceModel.Channels.SecurityBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="681d2-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
5. <span data-ttu-id="681d2-114">將原始的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 取代為來自 <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> 的啟動安裝安全性繫結項目。</span><span class="sxs-lookup"><span data-stu-id="681d2-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="681d2-115">範例</span><span class="sxs-lookup"><span data-stu-id="681d2-115">Example</span></span>  
 <span data-ttu-id="681d2-116">下列範例會建立了一個不包含安全工作階段的自訂聯合繫結。</span><span class="sxs-lookup"><span data-stu-id="681d2-116">This following example creates a custom federated binding without secure session.</span></span>  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="681d2-117">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="681d2-117">Compiling the Code</span></span>  
  
- <span data-ttu-id="681d2-118">若要編譯此程式碼範例，請建立一個可參考 System.ServiceModel.dll 組件的專案。</span><span class="sxs-lookup"><span data-stu-id="681d2-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681d2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="681d2-119">See also</span></span>

- [<span data-ttu-id="681d2-120">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="681d2-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
