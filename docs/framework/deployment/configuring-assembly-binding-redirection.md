---
title: 設定組件繫結重新導向
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e2add2756106234227c7b2dd62ae107adc58854
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052185"
---
# <a name="configuring-assembly-binding-redirection"></a>設定組件繫結重新導向
根據預設，應用程式會使用執行階段版本 (用來編譯應用程式) 隨附的 .NET Framework 組件集。 您可以使用應用程式組態檔中 [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) 項目上的 **appliesTo** 屬性，來重新導向組件繫結參考至特定版本的 .NET Framework 組件。 這個選擇性屬性會使用 .NET Framework 版本號碼，以表示它會套用至哪一個版本。 如果未指定 **appliesTo** 屬性，則 **\<assemblyBinding>** 項目會套用至所有的 .NET Framework 版本。  
  
 在 .NET Framework 1.1 版中引進了 **appliesTo** 屬性；而 .NET Framework 1.0 版則會忽略它。 這表示在使用 .NET Framework 1.0 版時，會套用所有 **\<assemblyBinding>** 項目，即使已指定 **appliesTo** 屬性時也是如此。  
  
> [!NOTE]
> 使用 **appliesTo** 屬性來限制組件繫結重新導向至特定版本的執行階段。  
  
 例如對於 .NET Framework 1.0 版組件，如果要重新導向組件繫結，您可在應用程式組態檔中包含下列 XML 程式碼。  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 **\<assemblyBinding>** 項目要區分順序。 您應先輸入任何 .NET Framework 1.0 版組件的組件繫結重新導向資訊，然後才是任何 .NET Framework 1.1 版組件的組件繫結重新導向資訊。 最後，請輸入不使用 **appliesTo** 屬性的任何 .NET Framework 組件重新導向之組件繫結重新導向資訊，如此一來會適用於所有版本的 .NET Framework。 若重新導向發生衝突，會使用組態檔中第一筆相符的重新導向陳述式。  
  
 例如，若要重新導向一個參考至 .NET Framework 1.0 版組件和另一個參考至 .NET Framework 1.1 版組件，則您可使用下列虛擬程式碼所示的模式。  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
  <!-- .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
  <!-- .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a>偵錯組態檔錯誤  
 一旦建立應用程式定義域，並載入程式碼至應用程式定義域中，執行階段就會剖析組態檔。 Common Language Runtime 會忽略此項目，以處理組態檔中的錯誤。 如果它包含格式不正確的 XML，則執行階段會略過整個組態檔案。 對於無效的 XML，則會忽略無效的區段。  
  
 您可判斷組態檔是否用於決定正在進行組件繫結重新導向。 使用[組件繫結記錄檔檢視器 (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) 來查看正在載入哪些組件。 若要查看所有組件繫結，您必須在登錄中設定 **ForceLog** 項目。  
  
## <a name="see-also"></a>另請參閱

- [如何：啟用和停用自動繫結重新導向](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
