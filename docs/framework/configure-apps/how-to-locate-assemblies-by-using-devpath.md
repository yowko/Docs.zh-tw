---
title: HOW TO：使用 DEVPATH 找出組件
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 5c4041f42b0a9d1d1e4bc8438e662911534daa42
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826677"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>HOW TO：使用 DEVPATH 找出組件
開發人員可能想要確定自己進行建置，某個共用組件與多個應用程式正常運作。 而不是持續將組件在全域組件快取中放在開發期間，開發人員可以建立指向組件的組建輸出目錄 DEVPATH 環境變數。  
  
 例如，假設您正在建置呼叫 MySharedAssembly 某個共用組件，並輸出目錄是 C:\MySharedAssembly\Debug。 您可以將 C:\MySharedAssembly\Debug 放在 DEVPATH 變數中。 然後您必須指定[ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)電腦組態檔中的項目。 這個項目會告知 common language runtime 使用 DEVPATH 找出組件。  
  
 共用的組件必須可由執行階段。  若要指定私用的目錄來解析組件的參考使用[\<程式碼基底 > 項目](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)或是[\<探查 > 項目](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)在組態檔中所述[指定組件的位置](../../../docs/framework/configure-apps/specify-assembly-location.md)。  您也可以將組件放在應用程式目錄的子目錄中。 如需詳細資訊，請參閱 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。  
  
> [!NOTE]
>  這是一項進階的功能，僅供開發。  
  
 下列範例示範如何讓執行階段搜尋 DEVPATH 環境變數所指定的目錄中的組件。  
  
## <a name="example"></a>範例  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 此設定預設為 false。  
  
> [!NOTE]
>  使用此設定只在開發階段。 執行階段不會檢查在 DEVPATH 中找到的強式名稱組件的版本。 它會直接使用第一個找到的組件。  
  
## <a name="see-also"></a>另請參閱

- [使用組態檔設定應用程式](index.md)
