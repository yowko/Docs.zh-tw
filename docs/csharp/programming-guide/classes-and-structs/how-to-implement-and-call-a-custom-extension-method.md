---
title: "如何：實作和呼叫自訂擴充方法 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a277412c69d26f20721381d9cfa839c7f082f2f2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>如何：實作和呼叫自訂擴充方法 (C# 程式設計手冊)
本主題示範如何針對任何 .NET 類型實作您自己的延伸模組方法。 用戶端程式碼可以使用您的擴充方法，方法是將參考新增至包含這些方法的 DLL，然後新增 [using](../../../csharp/language-reference/keywords/using-directive.md) 指示詞，以指定會在其中定義擴充方法的命名空間。  
  
## <a name="to-define-and-call-the-extension-method"></a>定義和呼叫擴充方法  
  
1.  定義靜態[類別](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)以包含擴充方法。  
  
     此類別對用戶端程式碼而言必須是可見的。 如需存取範圍規則的詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
2.  將擴充方法實作為其可見度至少等同於包含類別的靜態方法。  
  
3.  方法的第一個參數會指定方法的作業類型，前面必須加上 [this](../../../csharp/language-reference/keywords/this.md) 修飾詞。  
  
4.  在呼叫程式碼中，新增 `using` 指示詞以指定包含擴充方法類別的[命名空間](../../../csharp/language-reference/keywords/namespace.md)。  
  
5.  將方法當做是類型上的執行個體方法進行呼叫。  
  
     請注意，呼叫程式碼未指定第一個參數，因為它代表要套用運算子的類型，而且編譯器已知物件類型。 您只需要針對參數 2 到 `n` 提供引數。  
  
## <a name="example"></a>範例  
 下列範例會在 `CustomExtensions.StringExtension` 類別中實作名為 `WordCount` 的擴充方法。 此方法會用於指定為第一個方法參數的 <xref:System.String> 類別。 `CustomExtensions` 命名空間會匯入應用程式命名空間，並在 `Main` 方法內呼叫此方法。  
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此程式碼，請將它複製並貼至已在 [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] 中建立的 Visual C# 主控台應用程式專案。 根據預設，此專案是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版為目標，且有 System.Core.dll 的參考，以及 System.Linq 的 `using` 指示詞。 如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 擴充方法沒有特定安全性弱點。 它們無法用於模擬類型上的現有方法，因為所有名稱衝突已使用類型自行定義的執行個體或靜態方法解決。 擴充方法無法存取擴充類別中的任何私用資料。  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [this](../../../csharp/language-reference/keywords/this.md)  
 [命名空間](../../../csharp/language-reference/keywords/namespace.md)
