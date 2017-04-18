---
title: "自訂控制項中的方法實作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "使用者控制項 [Windows Form] 方法實作"
  - "多載方法的自訂控制項 [Windows Form]"
  - "自訂控制項 [Windows Form] 方法實作"
  - "方法 [Windows Form]"
  - "方法 [Windows Form] 自訂控制項"
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 自訂控制項中的方法實作
在控制項中實作方法的方式，與在其他任何元件中實作方法的方式相同。  
  
 在 Visual Basic 中，若方法必須傳回值，會實作為 `Public Function`。 若無須傳回值，便會實作為 `Public Sub`。 方法會透過下列語法宣告：  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 由於函式需要傳回值，因此必須指定傳回類型，例如 integer、string、object 等等。 程序如有接受引數 `Function` 或 `Sub`，也必須加以指定。  
  
 C# 的函式與程序與 Visual Basic 並無差別。 方法會傳回值或傳回 `void`。 以下是宣告 C# 公用方法的語法：  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 當您宣告方法時，應盡可能地將其所有引數宣告成明確的資料類型。 接受物件參考的引數應宣告為特定類型，例如應宣告為 `As Widget`，而不是 `As Object`。 在 Visual Basic 中，預設設定 `Option Strict` 會自動施行此規則。  
  
 宣告引數的類型有助於編譯器預先檢出許多開發人員的錯誤，而不是在執行時發生。 編譯器一律會檢查錯誤，而執行時期測試僅具備測試套件的功能。  
  
## <a name="overloaded-methods"></a>多載的方法  
 若要允許控制項的使用者提供不同的參數組合給方法，請使用明確的資料類型，為方法提供多個多載。 請避免建立宣告有可能會包含任何資料類型之 `As Object` 的參數，因為這可能會導致測試時無法檢出的錯誤。  
  
> [!NOTE]
>  常見於語言執行時期的通用資料為 `Object`，而不是 `Variant`。 `Variant` 已從語言中移除。  
  
 例如假設 `Spin` 控制項的 `Widget` 方法可能會允許直接指定微調的方向及速度，或指定其他角動量要被吸收的 `Widget` 物件：  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [事件](../../../../docs/standard/events/index.md)   
 [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)