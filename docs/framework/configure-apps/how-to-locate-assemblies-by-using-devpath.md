---
title: "如何：使用 DEVPATH 找出組件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 70448f7ce4c00274dde14bace603e5c8852bf148
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>如何：使用 DEVPATH 找出組件
開發人員可能想要確定他們建立的共用組件的多個應用程式正常運作。 而不是持續將組件在全域組件快取中，在開發期間，開發人員可以建立 DEVPATH 環境變數指向的組件的組建輸出目錄。  
  
 例如，假設您正在建置呼叫 MySharedAssembly 共用組件並輸出目錄是 C:\MySharedAssembly\Debug。 您可以將 C:\MySharedAssembly\Debug DEVPATH 變數中。 您必須指定[ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)電腦組態檔中的項目。 這個項目會告知 common language runtime 使用 DEVPATH 找出組件。  
  
 共用組件必須是由執行階段可探索。  若要指定私用來解析組件的參考使用目錄[\<程式碼基底 > 項目](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)或[\<探查 > 項目](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)在組態檔中所述[指定組件的位置](../../../docs/framework/configure-apps/specify-assembly-location.md)。  您也可以將組件放在應用程式目錄的子目錄中。 如需詳細資訊，請參閱 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
> [!NOTE]
>  這是一項進階的功能，僅供開發。  
  
 下列範例會示範如何使執行階段 DEVPATH 環境變數所指定的目錄中搜尋組件。  
  
## <a name="example"></a>範例  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 這項設定會預設為 false。  
  
> [!NOTE]
>  使用此設定只在開發階段。 執行階段不會檢查 DEVPATH 中找到的強式名稱組件上的版本。 它只會使用第一個找到的組件。  
  
## <a name="see-also"></a>另請參閱  
 [設定.NET Framework 應用程式](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
