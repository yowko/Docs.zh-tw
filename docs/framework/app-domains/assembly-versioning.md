---
title: 組件版本控制
ms.date: 03/30/2017
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd2714b8220b6c4255a08d09275a015ba3966fa9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744352"
---
# <a name="assembly-versioning"></a>組件版本控制
使用 Common Language Runtime 之組件的所有版本控制都是在組件層級進行的。 組件的特定版本和相依組件的版本是記錄在組件的資訊清單中。 Runtime 的預設版本原則為，除非被組態檔 (應用程式組態檔、發行者原則檔和電腦的系統管理員組態檔) 中的明確版本原則強制取代，否則應用程式只能搭配用來建置和測試它們的版本執行。  
  
> [!NOTE]
>  版本控制只能在具有強式名稱 (Strong Name) 的組件上進行。  
  
 Runtime 會執行以下幾個步驟來解析組件繫結要求：  
  
1.  檢查原始組件參考來判斷要繫結的組件版本。  
  
2.  檢查所有適用的組態檔來套用版本原則。  
  
3.  從原始組件參考和組態檔中指定的任何重新導向判斷正確的組件，並且判斷應該繫結至呼叫之組件的版本。  
  
4.  檢查全域組件快取、組態檔中指定的程式碼基底，然後使用[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)中說明的探查規則檢查應用程式的目錄和子目錄。  
  
 下圖所示即為這些步驟。  
  
 ![.assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")  
解析組件繫結要求  
  
 如需設定應用程式的詳細資訊，請參閱[設定應用程式](../../../docs/framework/configure-apps/index.md)。 如需繫結原則的詳細資訊，請參閱[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
## <a name="version-information"></a>版本資訊  
 每一組件有兩種表示版本資訊的不同方式：  
  
-   組件的版本號碼以及組件名稱和文化特性資訊，都是組件識別的一部分。 這個號碼是執行階段用來強制執行版本原則的，也是在執行階段時的型別解析過程中非常重要的一部分。  
  
-   資訊版本，為表示其他版本資訊的字串，它隨附於組件僅做為資訊用途。  
  
### <a name="assembly-version-number"></a>組件版本號碼  
 每一組件都有一個版本號碼做為其識別的一部分。 因此，兩個版本號碼不同的組件會被執行階段視為完全不同的組件。 這個版本號碼實際上會以下列格式表示為四個部分的字串：  
  
 \<主要版本>.\<次要版本>.\<組建編號>.\<修訂>  
  
 例如，在版本 1.5.1254.0 中，1 表示主要版本、5 是次要版本、1254 是組建編號，而 0 則是修訂編號。  
  
 版本號碼儲存在組件資訊清單中，其他識別資訊 (包括組件名稱和公開金鑰) 以及與應用程式連接的其他組件之關係和識別的相關資訊也一併儲存。  
  
 在建置組件時，開發工具會記錄組件資訊清單中所參考之每一組件的相依資訊。 Runtime 會使用這些版本號碼配合系統管理員、應用程式或發行者所設定的組態資訊來載入所參考之組件的適當版本。  
  
 Runtime 會針對版本的用途區別一般和強式名稱的組件。 版本檢查只會發生於強式名稱的組件。  
  
 如需指定版本繫結原則的資訊，請參閱[設定應用程式](../../../docs/framework/configure-apps/index.md)。 如需執行階段如何使用版本資訊找到特定組件的資訊，請參閱[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
### <a name="assembly-informational-version"></a>組件資訊版本  
 資訊版本是個將其他版本資訊附加到組件僅供資訊用途的字串；這項資訊不會在執行階段時使用。 文字架構的資訊版本會對應到該產品的行銷刊物、包裝或產品名稱，並且不會被執行階段使用。 例如，資訊版本可以是 "Common Language Runtime Version 1.0" 或 "NET Control SP 2"。 在 Microsoft Windows 中檔案 [內容] 對話方塊的 [版本] 索引標籤上，這項資訊會出現在 [產品版本] 項目之中。  
  
> [!NOTE]
>  儘管您可以指定任何文字，如果字串不屬於組件版本號碼所使用的格式，或是屬於這種格式卻包含萬用字元，在編譯時就會出現警告訊息。 這項警告是無害的。  
  
 資訊版本是使用自訂屬性 <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType> 表示。 如需資訊版本屬性的詳細資訊，請參閱[設定組件屬性](../../../docs/framework/app-domains/set-assembly-attributes.md)。  
  
## <a name="see-also"></a>請參閱  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [設定應用程式](../../../docs/framework/configure-apps/index.md)  
 [設定組件屬性](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
