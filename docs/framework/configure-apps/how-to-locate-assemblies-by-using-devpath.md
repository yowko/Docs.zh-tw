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
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912991"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>作法：使用 DEVPATH 找出組件
開發人員可能會想要確定它們所建立的共用元件能與多個應用程式正確搭配運作。 開發人員可以建立 DEVPATH 環境變數, 以指向元件的組建輸出目錄, 而不是在開發週期期間持續將元件放在全域組件快取中。  
  
 例如, 假設您要建立一個名為 MySharedAssembly 的共用元件, 而輸出目錄是 C:\MySharedAssembly\Debug。 您可以將 C:\MySharedAssembly\Debug 放在 DEVPATH 變數中。 接著, 您必須在電腦設定檔中指定[ \<developmentMode >](./file-schema/runtime/developmentmode-element.md)元素。 這個元素會告知 common language runtime 使用 DEVPATH 來尋找元件。  
  
 執行時間必須可探索共用元件。  若要指定解析元件參考的私用目錄, 請在設定檔中使用[ \<程式碼基底 > 元素](./file-schema/runtime/codebase-element.md)或[ \<探查 > 元素](./file-schema/runtime/probing-element.md), 如[指定元件的位置](specify-assembly-location.md)中所述。  您也可以將元件放在應用程式目錄的子目錄中。 如需詳細資訊，請參閱 [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)。  
  
> [!NOTE]
> 這是一項先進的功能, 僅供開發之用。  
  
 下列範例顯示如何讓執行時間在 DEVPATH 環境變數所指定的目錄中搜尋元件。  
  
## <a name="example"></a>範例  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 此設定的預設值為 false。  
  
> [!NOTE]
> 請只在開發階段使用此設定。 執行時間不會檢查在 DEVPATH 中找到的強式名稱元件上的版本。 它只會使用所找到的第一個元件。  
  
## <a name="see-also"></a>另請參閱

- [使用設定檔設定應用程式](index.md)
