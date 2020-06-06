---
title: 指定組件的位置
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646024"
---
# <a name="specifying-an-assemblys-location"></a>指定組件的位置
有兩種方式可以指定元件的位置：  
  
- 使用 [\<codeBase>](./file-schema/runtime/codebase-element.md) 元素。  
  
- 使用 [\<probing>](./file-schema/runtime/probing-element.md) 元素。  
  
 您也可以使用[.NET Framework 設定工具（mscorcfg.msc）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100))來指定元件位置，或指定 common language runtime 探查元件的位置。  
  
## <a name="using-the-codebase-element"></a>使用 \<codeBase> 元素  
 您 **\<codeBase>** 只能在電腦設定或發行者原則檔（也就是也會重新導向元件版本）中使用元素。 當執行時間決定要使用的元件版本時，它會從判斷版本的檔案套用程式碼基底設定。 如果沒有指定程式碼基底，執行時間會以正常方式探查元件。 如需詳細資訊，請參閱[執行時間如何找出元件](../deployment/how-the-runtime-locates-assemblies.md)。  
  
 下列範例顯示如何指定元件的位置。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 所有強式名稱元件都需要**version**屬性，但如果元件不是強式名稱，則應該予以省略。 **\<codeBase>** 元素需要**href**屬性。 您不能在元素中指定版本範圍 **\<codeBase>** 。  
  
> [!NOTE]
> 如果您為不是以強式名稱命名的元件提供程式碼基底提示，則提示必須指向應用程式基底目錄或應用程式基底目錄的子目錄。  
  
## <a name="using-the-probing-element"></a>使用 \<probing> 元素  
 執行時間會透過探查找出沒有程式碼基底的元件。 如需探查的詳細資訊，請參閱[執行時間如何找出元件](../deployment/how-the-runtime-locates-assemblies.md)。  
  
 您可以使用 [\<probing>](./file-schema/runtime/probing-element.md) 應用程式佈建檔中的專案，來指定執行時間在尋找元件時應搜尋的子目錄。 下列範例顯示如何指定執行時間應該搜尋的目錄。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath**屬性包含執行時間應該搜尋元件的目錄。 如果應用程式位於 C:\Program Files\MyApp，則執行時間會尋找未在 C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3. 中指定程式碼基底的元件 **PrivatePath**中指定的目錄必須是應用程式基底目錄的子目錄。  
  
## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../standard/assembly/index.md)
- [使用組件設計程式](../../standard/assembly/index.md)
- [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)
- [使用組態檔設定應用程式](index.md)
