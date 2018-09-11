---
title: '&lt;behaviorExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: d025497956715913923e839cb6c482f44f96babb
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261427"
---
# <a name="ltbehaviorextensionsgt"></a><span data-ttu-id="9e2e3-102">&lt;behaviorExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="9e2e3-102">&lt;behaviorExtensions&gt;</span></span>
<span data-ttu-id="9e2e3-103">行為延伸可讓使用者建立使用者定義的行為項目。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-103">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="9e2e3-104">這些項目可以和標準的 Windows Communication Foundation (WCF) 行為項目並列使用。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-104">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="9e2e3-105">`behaviorExtensions` 區段會定義項目，讓項目可用於組態中。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-105">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="9e2e3-106">以下是典型行為擴充的範例。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-106">Here is an example of a typical behavior extension.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="myBehavior" type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
       </behaviorExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9e2e3-107">若要將組態功能加入至項目，您必須寫入並註冊組態項目。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-107">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="9e2e3-108">如需這方面的詳細資訊，請參閱 <xref:System.Configuration>。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="9e2e3-109">在定義項目及其組態型別後，即可使用擴充，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-109">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
    <behavior configurationName="testChannelBehavior">  
        <myBehavior />  
        <channelSecurity cacheCookies="false" detectReplays="false" maxCachedNonces="9"  
            maxClockSkew="00:00:03" maxCookieCachingTime="00:07:24" replayWindow="00:07:22.2190000" />  
    </behavior>  
</behaviors>  
```  
  
## <a name="security"></a><span data-ttu-id="9e2e3-110">安全性</span><span class="sxs-lookup"><span data-stu-id="9e2e3-110">Security</span></span>  
 <span data-ttu-id="9e2e3-111">強烈建議您在 `machine.config` 和 `app.config` 檔案中註冊型別時，使用完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-111">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="9e2e3-112">如果型別不是唯一定義的型別，則 CLR 型別載入器會以指定的順序在以下位置中搜尋該型別：</span><span class="sxs-lookup"><span data-stu-id="9e2e3-112">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="9e2e3-113">如果型別的組件為已知，則載入器會搜尋組態檔案的重新導向位置、GAC、使用組態資訊的目前組件，和應用程式基底目錄。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-113">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="9e2e3-114">如果組件為未知，則載入器會搜尋目前組件、mscorlib 和 `TypeResolve` 事件處理常式傳回的位置。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-114">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="9e2e3-115">這個 CLR 搜尋順序可以用型別轉送機制和 AppDomain.TypeResolve 事件等攔截程序 (Hook) 來修改。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-115">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="9e2e3-116">攻擊者可能會利用 CLR 搜尋順序並執行未經授權的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-116">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="9e2e3-117">使用完整 (強式) 名稱來唯一識別型別，可進一步增加您系統的安全性。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-117">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="9e2e3-118">如需詳細資訊，請參閱 <<c0> [ 執行階段如何找出組件](https://go.microsoft.com/fwlink/?LinkId=95336)和<xref:System.AppDomain.TypeResolve>。</span><span class="sxs-lookup"><span data-stu-id="9e2e3-118">For more information, see [How the Runtime Locates Assemblies](https://go.microsoft.com/fwlink/?LinkId=95336) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e2e3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e2e3-119">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [<span data-ttu-id="9e2e3-120">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="9e2e3-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
