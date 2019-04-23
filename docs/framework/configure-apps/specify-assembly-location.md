---
title: 指定組件的位置
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: f7d09e315f2ccc7ecdcf22719ca6dce1ee1411b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186286"
---
# <a name="specifying-an-assemblys-location"></a>指定組件的位置
有兩種方式可指定組件的位置：  
  
-   使用[\<程式碼基底 >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)項目。  
  
-   使用[\<探查 >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)項目。  
  
 您也可以使用[.NET Framework 組態工具 (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100))來指定組件的位置，或指定通用語言執行平台，來探查組件的位置。  
  
## <a name="using-the-codebase-element"></a>使用\<程式碼基底 > 項目  
 您可以使用**\<程式碼基底 >** 只能在機器組態或發行者原則檔案，也將重新導向組件版本中的項目。 當執行階段判斷要使用的組件版本時，它適用於決定版本檔案的程式碼基底設定。 如果沒有程式碼基底指示，執行階段會以一般方式探查組件。 如需詳細資訊，請參閱 <<c0> [ 執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
 下列範例示範如何指定組件的位置。  
  
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
  
 **版本**屬性所需的所有強式名稱組件，但應該不是強式名稱的組件中省略。 **\<程式碼基底 >** 項目需要**href**屬性。 您不能指定版本範圍**\<程式碼基底 >** 項目。  
  
> [!NOTE]
>  如果您不是強式名稱組件提供的程式碼基底的提示，此提示必須指向應用程式基底或應用程式基底目錄的子目錄。  
  
## <a name="using-the-probing-element"></a>使用\<探查 > 項目  
 執行階段找出並沒有程式碼基底所探查的組件。 如需有關探查的詳細資訊，請參閱[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
 您可以使用[\<探查 >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)應用程式組態檔來指定執行階段尋找組件時，應該搜尋的子目錄中的項目。 下列範例示範如何指定執行階段應該搜尋的目錄。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **Bin**屬性包含執行階段應該搜尋組件的目錄。 如果應用程式位於 C:\Program Files\MyApp，執行階段會尋找組件不會在 C:\Program Files\MyApp\Bin、 C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3 中指定的程式碼基底。 中指定的目錄**Bin**必須是應用程式基底目錄的子目錄。  
  
## <a name="see-also"></a>另請參閱

- [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [使用組態檔設定應用程式](index.md)
