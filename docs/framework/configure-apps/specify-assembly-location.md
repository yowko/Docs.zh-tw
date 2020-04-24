---
title: 指定組件的位置
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646024"
---
# <a name="specifying-an-assemblys-location"></a>指定組件的位置
有兩種方法可以指定程式集的位置:  
  
- 使用[\<代碼庫>](./file-schema/runtime/codebase-element.md)元素。  
  
- 使用[\<探測>](./file-schema/runtime/probing-element.md)元素。  
  
 您還可以使用[.NET 框架設定工具 (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100))指定程式集位置或指定要探測程式集的通用語言執行時的位置。  
  
## <a name="using-the-codebase-element"></a>使用\<程式庫>元素  
 只能在電腦配置或發佈者策略檔中使用**\<codeBase>** 元素,這些檔也會重定向程式集版本。 當運行時確定要使用的程式集版本時,它將從確定版本的檔中應用代碼庫設置。 如果未指示代碼庫,則以正常方式探測程式集的運行時探測。 有關詳細資訊,請參閱[執行時如何尋找程式集](../deployment/how-the-runtime-locates-assemblies.md)。  
  
 下面的範例示範如何指定程式集的位置。  
  
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
  
 所有強命名程式集都需要**版本**屬性,但對於未強命名的程式集,應省略版本屬性。 代碼庫>元素需要**href**屬性。 ** \<** 不能在**\<代碼庫>** 元素中指定版本範圍。  
  
> [!NOTE]
> 如果要為未強命名的程式集提供代碼基提示,則提示必須指向應用程式基或應用程式基目錄的子目錄。  
  
## <a name="using-the-probing-element"></a>使用\<探測>元素  
 運行時通過探測查找沒有代碼庫的程式集。 有關偵測的詳細資訊,請參閱[執行時如何查找程式集](../deployment/how-the-runtime-locates-assemblies.md)。  
  
 可以使用應用程式設定檔中的[\<探測>](./file-schema/runtime/probing-element.md)元素來指定運行時在定位程式集時應搜索的子目錄。 下面的範例展示如何指定運行時應搜尋的目錄。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **專用 Path**屬性包含運行時應搜索程式集的目錄。 如果應用程式位於 C:_程式檔\MyApp,執行時將查找未在 C:*程式檔_MyApp_Bin、C:程式檔\MyApp_Subbin和 C:程式檔\MyApp_Bin3中指定代碼庫的程式集。 **在私有路徑**中指定的目錄必須是應用程式基礎目錄的子目錄。  
  
## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../standard/assembly/index.md)
- [使用組件設計程式](../../standard/assembly/index.md)
- [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)
- [使用組態檔設定應用程式](index.md)
