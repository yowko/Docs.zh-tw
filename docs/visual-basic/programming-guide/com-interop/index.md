---
title: "COM Interop (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, COM interop"
  - "COM interop, in Visual Basic"
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# COM Interop (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

元件物件模型 \(Component Object Model，COM\) 可讓物件將其功能公開 \(Expose\) 給其他元件和主應用程式 \(Host Application\)。  目前大多數的軟體都包含 COM 物件。  雖然 .NET 組件是新應用程式的最佳選擇，但有時候您還是可能需要採用 COM 物件。  這個章節涵蓋了與利用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 建立和使用 COM 物件相關聯的一些問題。  
  
## 在本節中  
 [Introduction to COM Interop](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 提供 COM 互通性的概觀。  
  
 [How to: Reference COM Objects from Visual Basic](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 涵蓋如何將參考加到具有型別程式庫的 COM 物件。  
  
 [How to: Work with ActiveX Controls](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 示範如何使用現有 ActiveX 控制項 \(Control\)，將功能加入至 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 工具箱。  
  
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 逐步說明呼叫屬於 Windows 作業系統一部分之 API 的過程。  
  
 [How to: Call Windows APIs](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 示範如何定義和呼叫 User32.dll 中的 `MessageBox` 函式。  
  
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 示範如何呼叫 Windows 函式具有不帶正負號的型別參數。  
  
 [Walkthrough: Creating COM Objects with Visual Basic](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 逐步說明使用及不使用 COM 類別樣板建立 COM 物件的過程。  
  
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 涵蓋在使用 COM 時可能遇到的一些問題。  
  
 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 提供如何在相同應用程式中使用 COM 物件和 .NET Framework 物件的概觀。  
  
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 說明如何使用現有的 COM 物件做為新物件的基礎。  
  
## 相關章節  
 [與 Unmanaged 程式碼互通](../Topic/Interoperating%20with%20Unmanaged%20Code.md)  
 說明 Common Language Runtime 提供的互通性服務。  
  
 [將 COM 元件公開給 .NET Framework](../Topic/Exposing%20COM%20Components%20to%20the%20.NET%20Framework.md)  
 說明透過 COM Interop 呼叫 COM 型別的過程。  
  
 [將 .NET Framework 元件公開給 COM](../Topic/Exposing%20.NET%20Framework%20Components%20to%20COM.md)  
 描述從 COM 準備和使用 Managed 型別。  
  
 [套用 Interop 屬性](../Topic/Applying%20Interop%20Attributes.md)  
 涵蓋了在使用 Unmanaged 程式碼時您可使用的屬性 \(Attribute\)。