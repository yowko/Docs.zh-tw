---
title: 適用於 Windows 市集應用程式之 .NET Framework 中的反映
description: 在適用于 Windows Store 應用程式的 .NET 中使用反映。 有一組反映類型和成員可用於 Windows Store 應用程式，可供完整的 .NET 使用。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
ms.openlocfilehash: 86bb633e97f0f88dc2a2a042b6897695a258cc3c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865264"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>適用於 Windows 市集應用程式之 .NET Framework 中的反映

從 .NET Framework 4.5 開始，.NET Framework 包含一組反映類型和成員，以便在 Windows 8.x 存放區應用程式中使用。 這些類型和成員提供於完整 .NET Framework，以及適用於 Windows 市集應用程式的 .NET。 本文件說明這些與其對應項目在 .NET Framework 4 和舊版之間的主要差異。  
  
 如果您要建立 Windows 8.x 存放區應用程式，您必須在適用于 Windows 8.x 存放區應用程式的 .NET 中使用反映類型和成員。 這些類型和成員也可用於 (但不是必要) 桌面應用程式，因此您可以對這兩種應用程式使用相同的程式碼。  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo 和組件載入  
 在適用于 Windows 8.x 存放區應用程式的 .NET 中， <xref:System.Reflection.TypeInfo> 類別包含 .NET Framework 4 類別的部分功能 <xref:System.Type> 。 <xref:System.Type> 物件代表類型定義的參考，而 <xref:System.Reflection.TypeInfo> 物件則代表類型定義本身。 這可讓您操作 <xref:System.Type> 物件，而不一定需要執行階段載入它們所參考的組件。 取得相關聯的 <xref:System.Reflection.TypeInfo> 物件會強制載入組件。  
  
 <xref:System.Reflection.TypeInfo>包含許多上可用的成員 <xref:System.Type> ，而 .net 中的許多反映屬性則適用于 Windows 8.X 存放區應用程式會傳回物件的集合 <xref:System.Reflection.TypeInfo> 。 若要從 <xref:System.Type> 物件取得 <xref:System.Reflection.TypeInfo> 物件，請使用 <xref:System.Reflection.IReflectableType.GetTypeInfo%2A> 方法。  
  
## <a name="query-methods"></a>查詢方法  
 在適用于 Windows 8.x 存放區應用程式的 .NET 中，您可以使用會傳回集合的反映屬性， <xref:System.Collections.Generic.IEnumerable%601> 而不是傳回陣列的方法。 反映內容可以針對大型組件或類型實作這些集合的消極式周遊。  
  
 反映屬性只傳回特定物件上宣告的方法，而不會周遊繼承樹狀結構。 此外，它們不會使用 <xref:System.Reflection.BindingFlags> 參數進行篩選。 相反地，篩選發生在使用者程式碼中，對傳回的集合使用 LINQ 查詢。 對於因執行階段而產生的反映物件 (例如，因為 `typeof(Object)`)，周遊繼承樹狀結構最佳的執行方式是使用 <xref:System.Reflection.RuntimeReflectionExtensions> 類別的 helper 方法。 來自自訂反映內容之物件的取用者不能使用這些方法，而且必須自行周遊繼承樹狀結構。  
  
## <a name="restrictions"></a>限制  
 在 Windows 8.x 存放區應用程式中，對某些 .NET Framework 類型和成員的存取會受到限制。 例如，您無法使用物件來呼叫 Windows 8.x Store 應用程式的 .NET 中未包含的 .NET Framework 方法 <xref:System.Reflection.MethodInfo> 。 此外，在 Windows 8.x 存放區應用程式的內容中，不被視為安全的特定類型和成員會被封鎖，如同 <xref:System.Runtime.InteropServices.Marshal> 和 <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> 成員。 這項限制只會影響 .NET Framework 類型和成員；您可以如常呼叫您的程式碼或協力廠商程式碼。  
  
## <a name="example"></a>範例  
 這個範例會在適用于 Windows 8.x 存放區應用程式的 .NET 中使用反映類型和成員，以抓取類型的方法和屬性 <xref:System.Globalization.Calendar> ，包括繼承的方法和屬性。 若要執行此程式碼，請將它貼到 Windows 8.x 存放區頁面的程式碼檔案中，其中包含名為 <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> 反映的專案中名為的控制項 `textblock1` 。 如果您在不同名稱的專案內貼上這段程式碼，只要確定您變更命名空間名稱以符合專案即可。  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [反射](reflection.md)
