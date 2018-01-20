---
title: "指定組件 &#39; s 位置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4cfe8752ce3a562e1e4b576c63b56ff56255ff62
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="specifying-an-assembly39s-location"></a>指定組件 &#39; s 位置
有兩種方式來指定組件的位置：  
  
-   使用[\<程式碼基底 >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)項目。  
  
-   使用[\<探查 >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)項目。  
  
 您也可以使用[.NET Framework 組態工具 (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764)來指定組件的位置，或指定的 common language runtime 來探查組件位置。  
  
## <a name="using-the-codebase-element"></a>使用\<程式碼基底 > 項目  
 您可以使用**\<程式碼基底 >**只能在電腦組態檔或發行者原則檔，也會重新導向組件版本中的項目。 當執行階段會判定要使用的組件版本時，它會套用決定版本的檔案的程式碼基底設定。 如果指示沒有程式碼基底，執行階段會以一般方式探查組件。 如需詳細資訊，請參閱[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
 下列範例會示範如何指定組件的位置。  
  
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
  
 **版本**屬性是必要的所有強式名稱組件，但應該省略不是強式名稱的組件。 **\<程式碼基底 >**元素需要**href**屬性。 您不能指定版本範圍中的**\<程式碼基底 >**項目。  
  
> [!NOTE]
>  如果您不是強式名稱組件提供的程式碼基底的提示，此提示必須指向應用程式基底或應用程式基底目錄的子目錄。  
  
## <a name="using-the-probing-element"></a>使用\<探查 > 項目  
 執行階段找出不需要程式碼基底探查的組件。 如需探查的詳細資訊，請參閱[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
 您可以使用[\<探查 >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)應用程式組態檔來指定執行階段尋找組件時，應該搜尋的子目錄中的項目。 下列範例會示範如何指定執行階段應該搜尋的目錄。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **Bin**屬性包含執行階段應該搜尋組件的目錄。 如果應用程式位於 C:\Program Files\MyApp，執行階段會尋找 C:\Program Files\MyApp\Bin、 C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3 中未指定程式碼基底的組件。 指定之目錄**Bin**必須是應用程式基底目錄的子目錄。  
  
## <a name="see-also"></a>請參閱  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [設定.NET Framework 應用程式](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
