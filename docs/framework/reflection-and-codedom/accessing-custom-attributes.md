---
title: 存取自訂屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb537950ce240d77282551f847b637a77792a264
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645232"
---
# <a name="accessing-custom-attributes"></a>存取自訂屬性
建立屬性與程式項目的關聯之後，就可以使用反映來查詢其存在狀況和值。 在 .NET Framework 1.0 和 1.1 版中，會檢查執行內容中的自訂屬性。 .NET Framework 2.0 版提供新的載入內容，就是僅限反映的內容，這可以用來檢查無法載入來執行的程式碼。  
  
## <a name="the-reflection-only-context"></a>僅限反映的內容  
 無法執行載入僅限反映內容的程式碼。 這表示無法建立自訂屬性的執行個體，因為這將需要執行其建構函式。 若要載入和檢查僅限反映內容中的自訂屬性，請使用 <xref:System.Reflection.CustomAttributeData> 類別。 您可以使用靜態 <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> 方法的適當多載，以取得此類別的執行個體。 請參閱[如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。  
  
## <a name="the-execution-context"></a>執行內容  
 查詢執行內容中屬性的主要反映方法是 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> 和 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>。  
  
 會檢查自訂屬性有關附加組件的存取性。 這相當於檢查附加自訂屬性中組件內之類型的方法是否可以呼叫自訂屬性的建構函式。  
  
 <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> 這類方法會檢查型別引數的可視性和存取性。 只有包含使用者定義型別之組件中的程式碼才能使用 **GetCustomAttributes** 擷取類型的自訂屬性。  
  
 下列 C# 範例是典型自訂屬性設計模式。 它會說明執行階段自訂屬性反映模型。  
  
```  
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 如果執行階段嘗試擷取附加至 **GetLanguage** 方法之公開自訂屬性類型 <xref:System.ComponentModel.DescriptionAttribute> 的自訂屬性，則會執行下列動作：  
  
1.  執行階段會檢查 **Type.GetCustomAttributes** 的型別引數 **DescriptionAttribute** (鍵入 *type*) 是公用的，因此可見且可供存取。  
  
2.  執行階段會檢查衍生自 **DescriptionAttribute** 的使用者定義型別 **MyDescriptionAttribute** 是否可以在 **System.Web.DLL** 組件內顯示和存取，其中，它會附加至 **GetLanguage**() 方法。  
  
3.  執行階段會檢查 **System.Web.DLL** 組件內 **MyDescriptionAttribute** 的建構函式可見且可供存取。  
  
4.  執行階段會使用自訂屬性參數來呼叫 **MyDescriptionAttribute** 的建構函式，並將新物件傳回給呼叫者。  
  
 自訂屬性反映模型可能會流失在其中定義使用者定義型別之組件外部的類型執行個體。 這與傳回使用者定義型別執行個體的執行階段系統程式庫成員沒有差異，例如 <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> 傳回 **RuntimeMethodInfo** 物件的陣列。 若要防止用戶端探索使用者定義自訂屬性類型的資訊，請將類型的成員定義為非公用。  
  
 下列範例示範如何使用反映來存取自訂屬性的基本方式。  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [反映的安全性考量](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
