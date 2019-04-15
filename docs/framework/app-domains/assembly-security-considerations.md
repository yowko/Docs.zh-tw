---
title: 組件安全性考量
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], security
- signcodes
- names [.NET Framework], assemblies
- strong-named assemblies, security considerations
- signing assemblies
- assemblies [.NET Framework], signing
- granting permissions, assemblies
- assemblies [.NET Framework], strong-named
- names [.NET Framework], strong names
- permissions [.NET Framework], assemblies
- security [.NET Framework], assemblies
- integrity with assemblies
ms.assetid: 1b5439c1-f3d5-4529-bd69-01814703d067
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e74d7a4a72b9595d6a280a16ad9bbc4118648404
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218066"
---
# <a name="assembly-security-considerations"></a>組件安全性考量
<a name="top"></a> 當您建置組件時，您可以指定一組該組件需要用來執行的使用權限。 是否將某些使用權限授予組件則以辨識項 (Evidence) 為基礎。  
  
 使用辨識項有兩種不同的方法：  
  
-   輸入辨識項會和載入器所集合的辨識項合併，以建立用於原則解析的最終辨識項組。 使用這個語意的方法包括 **Assembly.Load**、**Assembly.LoadFrom** 和 **Activator.CreateInstance**。  
  
-   輸入辨識項使用時不會更改，就和用於原則解析的最終辨識項組一樣。 使用這個語意的方法包括 **Assembly.Load(byte[])** 和 **AppDomain.DefineDynamicAssembly()**。  
  
 選擇性的使用權限可以藉由該組件要在其上執行之電腦上所設定的[安全性原則](../../../docs/framework/misc/code-access-security-basics.md)來授與。 如果您希望程式碼處理所有可能的安全性例外狀況，您可以執行下列某一項動作：  
  
-   插入您程式碼必須擁有之所有使用權限的使用權限要求，並且處理萬一使用權限未獲授予時，發生在最前面位置的載入期間失敗。  
  
-   不要利用使用權限要求來取得程式碼可能需要的使用權限，但是要準備處理萬一使用權限未獲授予時的安全性例外狀況。  
  
    > [!NOTE]
    >  安全性是個複雜的領域，有許多的選項可以供您選擇。 如需詳細資訊，請參閱[重要的安全性概念](../../../docs/standard/security/key-security-concepts.md)。  
  
 在載入期間，組件的辨識項 (Evidence) 是用來做為安全性原則的輸入。 安全性原則是由企業和電腦的系統管理員以及使用者原則設定所建立的，它決定在執行時授予所有 Managed 程式碼的使用權限集。 安全性原則可以針對組件 (如果具有簽署工具產生的簽章) 的發行者、針對要從其中下載組件的 Web 網站和區域 (Internet Explorer 的用詞)，或針對組件的強式名稱 (Strong Name) 建立。 例如，電腦的系統管理員可以建立安全性原則，允許從某一 Web 網站下載並且由特定軟體公司簽名的所有程式碼存取電腦上的某個資料庫，但是不授予寫入該電腦磁碟的存取權。  
  
## <a name="strong-named-assemblies-and-signing-tools"></a>強式名稱組件和簽署工具  

 > [!WARNING]
 > 請勿依賴強式名稱提供安全性。 強式名稱僅提供唯一識別。

 您可以用兩種不同但互補的方式來簽署組件：運用強式名稱，或是使用 [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md)。 使用強式名稱簽署組件，就會將公開金鑰加密新增至含有組件資訊清單的檔案。 強式名稱簽署可協助驗證唯一名稱，防止冒用名稱，並且在解析參考時為呼叫端提供某種識別 (Identity)。  
  
 並沒有任何信任層級與強式名稱建立關聯，這也使得 [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md) 更為重要。 這兩種簽署工具需要發行者向協力廠商授權單位證明其識別並取得憑證。 然後將這項憑證嵌入您的檔案，就可以讓系統管理員用來決定是否要信任程式碼的真實性。  
  
 您可以同時對組件賦予強式名稱和使用 [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md) 建立的數位簽章，或是只使用其中一種。 這兩種簽署工具只能同時簽署一個檔案。對於多檔案組件，您必須簽署含有組件資訊清單的檔案。 強式名稱儲存在包含組件資訊清單的檔案中，但是使用 [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md) 建立的簽章，則是儲存在包含組件資訊清單的可攜式執行檔 (PE) 中的保留位置。 當您已經擁有依靠 [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md) 所產生簽章的信任階層，或者您的原則只使用金鑰部分而不檢查信任鏈結，您就能使用 [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md) 來簽署組件 (不論是否使用強式名稱)。  
  
> [!NOTE]
>  在組件上同時使用強式名稱和簽署工具簽章時，必須先指定強式名稱。  
  
 Common Language Runtime 也會執行雜湊驗證；組件資訊清單包含構成組件的所有檔案清單，包括建置資訊清單時所在的每一個檔案的雜湊。 載入每一個檔案時，它的內容會被雜湊並且與資訊清單中儲存的雜湊值進行比對。 如果兩個雜湊不相符，就無法載入組件。  
  
 由於強式命名和使用 [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md) 的簽署可保證完整性，所以您可以讓程式碼存取安全性原則以這兩種形式的組件辨識項作為基礎。 強式命名和使用 [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md) 的簽署，可以透過數位簽章和憑證來保證完整性。 所有前述技術 (雜湊驗證、強式命名和使用 [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md) 的簽署)，合在一起即可確保組件沒有以任何方式改變。  
  
## <a name="see-also"></a>另請參閱

- [強式名稱的組件](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [SignTool.exe (簽署工具)](../../../docs/framework/tools/signtool-exe.md)
