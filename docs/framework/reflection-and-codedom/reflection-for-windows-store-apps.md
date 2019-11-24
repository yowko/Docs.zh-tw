---
title: 適用於 Windows 市集應用程式之 .NET Framework 中的反映
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9aaec282fda0a038d14f3a0cd57e1a8a2855f2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448140"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>適用於 Windows 市集應用程式之 .NET Framework 中的反映

Starting with the .NET Framework 4.5, the .NET Framework includes a set of reflection types and members for use in Windows 8.x Store apps. These types and members are available in the full .NET Framework as well as in the .NET for Windows Store apps. 本文件說明這些與其對應項目在 .NET Framework 4 和舊版之間的主要差異。  
  
 If you are creating a Windows 8.x Store app, you must use the reflection types and members in the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. 這些類型和成員也可用於 (但不是必要) 桌面應用程式，因此您可以對這兩種應用程式使用相同的程式碼。  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo 和組件載入  
 在 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 中，<xref:System.Reflection.TypeInfo> 類別包含 .NET Framework 4 <xref:System.Type> 類別的某些功能。 <xref:System.Type> 物件代表類型定義的參考，而 <xref:System.Reflection.TypeInfo> 物件則代表類型定義本身。 這可讓您操作 <xref:System.Type> 物件，而不一定需要執行階段載入它們所參考的組件。 取得相關聯的 <xref:System.Reflection.TypeInfo> 物件會強制載入組件。  
  
 <xref:System.Reflection.TypeInfo> 包含許多 <xref:System.Type> 上可用的成員，而 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 中的許多反映屬性會傳回 <xref:System.Reflection.TypeInfo> 物件的集合。 若要從 <xref:System.Type> 物件取得 <xref:System.Reflection.TypeInfo> 物件，請使用 <xref:System.Reflection.IReflectableType.GetTypeInfo%2A> 方法。  
  
## <a name="query-methods"></a>查詢方法  
 在 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 中，請使用會傳回 <xref:System.Collections.Generic.IEnumerable%601> 集合的反映屬性，而不要使用傳回陣列的方法。 反映內容可以針對大型組件或類型實作這些集合的消極式周遊。  
  
 反映屬性只傳回特定物件上宣告的方法，而不會周遊繼承樹狀結構。 此外，它們不會使用 <xref:System.Reflection.BindingFlags> 參數進行篩選。 相反地，篩選發生在使用者程式碼中，對傳回的集合使用 LINQ 查詢。 對於因執行階段而產生的反映物件 (例如，因為 `typeof(Object)`)，周遊繼承樹狀結構最佳的執行方式是使用 <xref:System.Reflection.RuntimeReflectionExtensions> 類別的 helper 方法。 來自自訂反映內容之物件的取用者不能使用這些方法，而且必須自行周遊繼承樹狀結構。  
  
## <a name="restrictions"></a>限制  
 In a Windows 8.x Store app, access to some .NET Framework types and members is restricted. 例如，您不能藉由使用 <xref:System.Reflection.MethodInfo> 物件，呼叫未包含在 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 的 .NET Framework 方法。 In addition, certain types and members that are not considered safe within the context of a Windows 8.x Store app are blocked, as are <xref:System.Runtime.InteropServices.Marshal> and <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> members. 這項限制只會影響 .NET Framework 類型和成員；您可以如常呼叫您的程式碼或協力廠商程式碼。  
  
## <a name="example"></a>範例  
 此範例使用 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 中的反映類型和成員來擷取 <xref:System.Globalization.Calendar> 類型的方法和屬性，包括繼承的方法和屬性。 To run this code, paste it into the code file for a Windows 8.x Store page that contains a <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> control named `textblock1` in a project named Reflection. 如果您在不同名稱的專案內貼上這段程式碼，只要確定您變更命名空間名稱以符合專案即可。  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>請參閱

- [反映](reflection.md)
