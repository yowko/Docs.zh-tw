---
title: 指定組件的位置
description: 請參閱如何使用程式碼基底元素或 XML 設定檔中的探查專案，在 .NET 中指定元件的位置。
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 6f9e41584ca36fcead06b73a485cb879c45705fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166881"
---
# <a name="specifying-an-assemblys-location"></a>指定組件的位置

有兩種方式可以指定元件的位置：  
  
- 使用 [\<codeBase>](./file-schema/runtime/codebase-element.md) 元素。  
  
- 使用 [\<probing>](./file-schema/runtime/probing-element.md) 元素。  
  
 您也可以使用 [.NET Framework 設定工具 (mscorcfg.msc) ](/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) 指定元件位置，或指定 common language runtime 探查元件的位置。  
  
## <a name="using-the-codebase-element"></a>使用 \<codeBase> 元素  

 您 **\<codeBase>** 只能在電腦設定或發行者原則檔中使用專案，也會重新導向元件版本。 當執行時間判斷要使用的元件版本時，會從決定版本的檔案套用程式碼基底設定。 如果未指示任何程式碼基底，則執行時間會以一般方式探查元件。 如需詳細資訊，請參閱 [執行時間如何找出元件](../deployment/how-the-runtime-locates-assemblies.md)。  
  
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
  
 所有強式名稱元件都必須要有 **version** 屬性，但是針對未強式名稱的元件，則應該省略。 **\<codeBase>** 元素需要**href**屬性。 您無法在元素中指定版本範圍 **\<codeBase>** 。  
  
> [!NOTE]
> 如果您要為不是強式名稱的元件提供程式碼基底提示，則提示必須指向應用程式基底或應用程式基底目錄的子目錄。  
  
## <a name="using-the-probing-element"></a>使用 \<probing> 元素  

 執行時間會找出不具程式碼基底的元件（藉由探查）。 如需探查的詳細資訊，請參閱 [執行時間如何找出元件](../deployment/how-the-runtime-locates-assemblies.md)。  
  
 您可以使用 [\<probing>](./file-schema/runtime/probing-element.md) 應用程式佈建檔中的專案，指定在尋找元件時，執行時間應搜尋的子目錄。 下列範例顯示如何指定執行時間應搜尋的目錄。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath**屬性包含執行時間應搜尋元件的目錄。 如果應用程式位於 C:\Program Files\MyApp，則執行時間會尋找未在 C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3. 中指定程式碼基底的元件 **PrivatePath**中指定的目錄必須是應用程式基底目錄的子目錄。  
  
## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../standard/assembly/index.md)
- [使用組件設計程式](../../standard/assembly/index.md)
- [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)
- [使用組態檔設定應用程式](index.md)
