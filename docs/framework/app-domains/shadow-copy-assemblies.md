---
title: "陰影複製組件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9ca1f68b7f88c3aec08d58fc1ccba7ea082bb026
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="shadow-copying-assemblies"></a>陰影複製組件
陰影複製可讓應用程式定義域中使用的組件更新，而不需卸載應用程式定義域。 這對必須連續運作的應用程式特別有用，例如 ASP.NET 網站。  
  
> [!IMPORTANT]
>  [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式不支援陰影複製。  
  
 Common Language Runtime 在載入組件時會鎖定組件檔案，因此在卸載組件之前無法更新檔案。 若要從應用程式定義域卸載組件，唯一的方式為卸載應用程式定義域，如此在正常情況下，就無法在磁碟上更新組件，直到使用組件的所有應用程式定義域已卸載為止。  
  
 當設定應用程式定義域來陰影複製檔案時，會從應用程式路徑複製組件到另一個位置，並從該位置載入。 複本會遭到鎖定，但原始組件檔已解除鎖定，而且可以更新。  
  
> [!IMPORTANT]
>  唯一可以進行陰影複製的組件是儲存在應用程式目錄或其子目錄的，在設定應用程式定義域時可由 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A> 屬性指定。 儲存在全域組件快取的組件不會進行陰影複製。  
  
 本文包含下列章節：  
  
-   [啟用和使用陰影複製](#EnablingAndUsing)描述基本的用法，以及陰影複製可用的選項。  
  
-   [啟動效能](#StartupPerformance)描述為了在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中陰影複製而進行的變更，以改善啟動效能，也描述如何還原為舊版的行為。  
  
-   [已淘汰的方法](#ObsoleteMethods)描述對於 [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] 中控制陰影複製之屬性和方法的變更。  
  
<a name="EnablingAndUsing"></a>   
## <a name="enabling-and-using-shadow-copying"></a>啟用及使用陰影複製  
 您可以使用 <xref:System.AppDomainSetup> 類別的屬性，如下所示，設定用於陰影複製的應用程式定義域：  
  
-   將 <xref:System.AppDomainSetup.ShadowCopyFiles%2A> 屬性設為字串值 `"true"` 來啟用陰影複製。  
  
     根據預設，在載入組件之前，此設定會複製在應用程式路徑的所有組件到下載快取。 這與 Common Language Runtime 所維護的快取相同，用以儲存從其他電腦下載的檔案，而且當這些檔案不再必需時，Common Language Runtime 會自動刪除這些檔案。  
  
-   使用 <xref:System.AppDomainSetup.CachePath%2A> 屬性和 <xref:System.AppDomainSetup.ApplicationName%2A> 屬性，選擇性地設定用於陰影複製檔案的自訂位置。  
  
     藉由串連 <xref:System.AppDomainSetup.ApplicationName%2A> 屬性至 <xref:System.AppDomainSetup.CachePath%2A> 屬性做為子目錄，形成此位置的基底路徑。 這會陰影複製組件到這個路徑的子目錄，而非本身的基底路徑。  
  
    > [!NOTE]
    >  如果未設定 <xref:System.AppDomainSetup.ApplicationName%2A> 屬性，則會忽略 <xref:System.AppDomainSetup.CachePath%2A> 屬性，並使用下載快取。 不會有例外狀況擲回。  
  
     如果您指定自訂位置，則當您不再需要檔案時，要負責清除目錄及複製檔案。 它們不會自動刪除。  
  
     有幾個理由可能會讓您想設定陰影複製檔案的自訂位置。 如果您的應用程式會產生大量的複本，則您可能會想要設定陰影複製檔案的自訂位置。 下載快取會受大小所限制，而非存留期，因此 Common Language Runtime 很可能會嘗試刪除仍在使用中的檔案。 設定自訂位置的另一個理由是執行您應用程式的使用者沒有寫入權限，來寫入 Common Language Runtime 為下載快取所使用的目錄位置。  
  
-   使用 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 屬性來選擇性地限制陰影複製的組件。  
  
     當您啟用應用程式定義域的陰影複製時，預設會複製所有組件到應用程式路徑中；也就是 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A> 屬性所指定的目錄中。 您可以藉由建立字串限制所選目錄的複製，該字串只包含您想要陰影複製的目錄，並指派字串至 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 屬性。 請以分號分隔目錄。 只會對在所選目錄中的組件陰影複製。  
  
    > [!NOTE]
    >  如果您不指派字串給 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 屬性，或如果您將這個屬性設定為 `null`，則會陰影複製 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A> 屬性所指定目錄中的所有組件。  
  
    > [!IMPORTANT]
    >  目錄路徑不可包含分號，因為分號是分隔符號字元。 分號沒有逸出字元。  
  
<a name="StartupPerformance"></a>   
## <a name="startup-performance"></a>啟動效能  
 當使用陰影複製的應用程式定義域啟動時，複製應用程式目錄中的組件到陰影複製目錄會有延遲；或當組件已經在該位置時，驗證組件也會有延遲。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 之前，會複製所有組件到暫存目錄。 會開啟每個組件來確認組件名稱，且會驗證強式名稱。 會檢查每個組件，以查看它是否已更新為比陰影複製目錄中的複本還要新。 若是如此，則將它複製到陰影複製目錄中。 最後會捨棄暫時複本。  
  
 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，預設啟動行為會直接比較應用程式目錄中每個組件的檔案日期和時間以及陰影複製目錄中複本的檔案日期和時間。 如果已更新組件，便會使用和舊版 .NET Framework 相同的程序複製組件；否則會載入陰影複製目錄中的複本。  
  
 對於組件不常變更，且變更通常發生在組件一小部分的應用程式而言，會產生最大的效能改進。 如果應用程式中大部分的組件經常變更，則新的預設行為可能會導致效能變差。 您可以藉由將 [\<shadowCopyVerifyByTimestamp> 項目](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) (並設定 `enabled="false"`) 新增至組態檔，還原舊版 .NET Framework 的啟動行為。  
  
<a name="ObsoleteMethods"></a>   
## <a name="obsolete-methods"></a>已淘汰的方法  
 <xref:System.AppDomain> 類別有幾種方法，例如 <xref:System.AppDomain.SetShadowCopyFiles%2A> 和 <xref:System.AppDomain.ClearShadowCopyPath%2A>，可用來控制應用程式定義域上的陰影複製，但這些已經在 .NET Framework 2.0 版中標記為已淘汰。 建議使用 <xref:System.AppDomainSetup> 類別的屬性來設定用於陰影複製的應用程式定義域。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=fullName>   
 <xref:System.AppDomainSetup.CachePath%2A?displayProperty=fullName>   
 <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=fullName>   
 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=fullName>   
 [\<shadowCopyVerifyByTimestamp> 項目](../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)

