---
title: ".NET Framework 4.5.2 中的重定目標變更 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2be2a828-9052-4738-a965-d4a836cc6384
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 10af942724ce0207bc6e64f1ebabfdcd2d3488bd
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="retargeting-changes-in-the-net-framework-452"></a>.NET Framework 4.5.2 中的重定目標變更
在某些罕見的情況下，重定目標變更可能會影響以 .NET Framework 4.5.2 為目標來重新編譯的應用程式。 除非在下表中另有指定，否則這些變更不會影響以舊版 .NET Framework 為目標但在 4.5.2 版下執行的二進位檔。 .NET Framework 4.5.2 包含下列領域的重定目標變更：  
  
-   [Entity Framework](#EF)  
  
-   [Windows Forms](#WinForms)  
  
<a name="EF"></a>   
## <a name="entity-framework-retargeting-changes"></a>Entity Framework 重定目標變更  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|使用未排序的限制作業時，查詢更簡單|產生 `JOIN` 陳述式並包含限制作業呼叫 (不先使用 <xref:System.Data.Objects.ObjectQuery%601.OrderBy%2A>) 的查詢，現在能產生更簡單的 SQL。 升級至 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之後，這些查詢會產生比舊版更複雜的 SQL。|預設已停用這項功能。 如果 Entity Framework 產生額外的 `JOIN` 陳述式而造成效能降低，您可以啟用這項功能，方法是在應用程式組態檔 (app.config) 的 `<appSettings>` 區段中加入下列項目：<br /><br /> `<add key="EntityFramework_SimplifyLimitOperations" value="true" />`|次要|  
  
<a name="WinForms"></a>   
## <a name="windows-forms-retargeting-changes"></a>Windows Form 重定目標變更  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|使用 <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=fullName> 方法從 [剪貼簿] 擷取 HTML 格式的資料|若為以 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 為目標的應用程式，或者在 .NET Framework 4.5.1 或舊版上執行的應用程式，<xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=fullName> 會以 ASCII 字串形式來擷取 HTML 格式的資料。 因此，非 ASCII 字元 (ASCII 碼大於 0x7F 的字元) 會以兩個隨機字元表示。 例如，é (0xE9) 會以 Ã© (0xC3 0xA9) 表示。<br /><br /> 若為以 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 或更新版本為目標並且在 .NET Framework 4.5.2 上執行的應用程式，<xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=fullName> 會以 UTF-8 形式來擷取 HTML 格式的資料，以正確地表示大於 0x7F 的字元。|如果針對 HTML 格式字串的編碼問題實作了解決方法 (例如將從 [剪貼簿] 擷取的 HTML 字串傳遞至 <xref:System.Text.UTF8Encoding.GetString%2A?displayProperty=fullName> 方法以明確將其編碼)，並將目標從應用程式 4 版重定為 4.5 版，則應該移除該解決方法。|次要|  
  
## <a name="see-also"></a>另請參閱  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-2.md)   
 [4.5 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.5.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)
