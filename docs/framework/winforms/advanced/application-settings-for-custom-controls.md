---
title: 自訂控制項的應用程式設定
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: a4e477ce1c171b514482623595b2c5565564a2cb
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040465"
---
# <a name="application-settings-for-custom-controls"></a><span data-ttu-id="76153-102">自訂控制項的應用程式設定</span><span class="sxs-lookup"><span data-stu-id="76153-102">Application Settings for Custom Controls</span></span>
<span data-ttu-id="76153-103">當控制項裝載于協力廠商應用程式時, 您必須完成特定工作, 讓您的自訂控制項能夠保存應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="76153-103">You must complete certain tasks to give your custom controls the ability to persist application settings when the controls are hosted in third-party applications.</span></span>

 <span data-ttu-id="76153-104">大部分關於應用程式設定功能的檔, 都是根據您建立獨立應用程式的假設而撰寫。</span><span class="sxs-lookup"><span data-stu-id="76153-104">Most of the documentation about the Application Settings feature is written under the assumption that you are creating a standalone application.</span></span> <span data-ttu-id="76153-105">不過, 如果您要建立其他開發人員將裝載于其應用程式中的控制項, 您必須採取一些額外的步驟, 讓您的控制項正確保存其設定。</span><span class="sxs-lookup"><span data-stu-id="76153-105">However, if you are creating a control that other developers will host in their applications, you need to take a few additional steps for your control to persist its settings properly.</span></span>

## <a name="application-settings-and-custom-controls"></a><span data-ttu-id="76153-106">應用程式設定和自訂控制項</span><span class="sxs-lookup"><span data-stu-id="76153-106">Application Settings and Custom Controls</span></span>
 <span data-ttu-id="76153-107">為了讓您的控制項正確保存其設定, 它必須建立自己專用的應用程式設定包裝函式類別 (衍生自<xref:System.Configuration.ApplicationSettingsBase>), 以封裝進程。</span><span class="sxs-lookup"><span data-stu-id="76153-107">For your control to properly persist its settings, it must encapsulate the process by creating its own dedicated applications settings wrapper class, derived from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="76153-108">此外, 主要控制項類別必須執行<xref:System.Configuration.IPersistComponentSettings>。</span><span class="sxs-lookup"><span data-stu-id="76153-108">Additionally, the main control class must implement the <xref:System.Configuration.IPersistComponentSettings>.</span></span> <span data-ttu-id="76153-109">介面包含數個屬性, 以及兩個方法: <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>和<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>。</span><span class="sxs-lookup"><span data-stu-id="76153-109">The interface contains several properties as well as two methods, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> and <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>.</span></span> <span data-ttu-id="76153-110">如果您使用 Visual Studio 中的**Windows Form 設計工具**將控制項加入表單中, Windows Forms 會在<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>控制項初始化時自動呼叫; 您必須在控制項<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>的`Dispose`方法中呼叫自己。</span><span class="sxs-lookup"><span data-stu-id="76153-110">If you add your control to a form using the **Windows Forms Designer** in Visual Studio, Windows Forms will call <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automatically when the control is initialized; you must call <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> yourself in the `Dispose` method of your control.</span></span>

 <span data-ttu-id="76153-111">此外, 您應該執行下列動作, 讓自訂控制項的應用程式設定在設計階段環境 (例如 Visual Studio) 中正常運作:</span><span class="sxs-lookup"><span data-stu-id="76153-111">In addition, you should implement the following in order for application settings for custom controls to work properly in design-time environments such as Visual Studio:</span></span>

1. <span data-ttu-id="76153-112">自訂應用程式設定類別, 其中包含採用做<xref:System.ComponentModel.IComponent>為單一參數的函式。</span><span class="sxs-lookup"><span data-stu-id="76153-112">A custom application settings class with a constructor that takes an <xref:System.ComponentModel.IComponent> as a single parameter.</span></span> <span data-ttu-id="76153-113">使用此類別來儲存和載入所有的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="76153-113">Use this class to save and load all of your application settings.</span></span> <span data-ttu-id="76153-114">當您建立這個類別的新實例時, 請使用此函式來傳遞您的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="76153-114">When you create a new instance of this class, pass your custom control using the constructor.</span></span>

2. <span data-ttu-id="76153-115">建立此自訂設定類別之後, 在表單上建立並放置控制項, 例如表單的<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="76153-115">Create this custom settings class after the control has been created and placed on a form, such as in the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>

 <span data-ttu-id="76153-116">如需建立自訂設定類別的指示, [請參閱如何:建立應用程式](how-to-create-application-settings.md)設定。</span><span class="sxs-lookup"><span data-stu-id="76153-116">For instructions on creating a custom settings class, see [How to: Create Application Settings](how-to-create-application-settings.md).</span></span>

## <a name="settings-keys-and-shared-settings"></a><span data-ttu-id="76153-117">設定機碼和共用設定</span><span class="sxs-lookup"><span data-stu-id="76153-117">Settings Keys and Shared Settings</span></span>
 <span data-ttu-id="76153-118">有些控制項可以在同一個表單中多次使用。</span><span class="sxs-lookup"><span data-stu-id="76153-118">Some controls can be used multiple times within the same form.</span></span> <span data-ttu-id="76153-119">在大部分的情況下, 您會想要讓這些控制項保存自己的個別設定。</span><span class="sxs-lookup"><span data-stu-id="76153-119">Most of the time, you will want these controls to persist their own individual settings.</span></span> <span data-ttu-id="76153-120">使用上<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> <xref:System.Configuration.IPersistComponentSettings>的屬性時, 您可以提供唯一的字串, 其可在表單上區分控制項的多個版本。</span><span class="sxs-lookup"><span data-stu-id="76153-120">With the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> property on <xref:System.Configuration.IPersistComponentSettings>, you can supply a unique string that acts to disambiguate multiple versions of a control on a form.</span></span>

 <span data-ttu-id="76153-121">最簡單的方法<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>是<xref:System.Windows.Forms.Control.Name%2A>使用的控制項<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="76153-121">The simplest way to implement <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> is to use the <xref:System.Windows.Forms.Control.Name%2A> property of the control for the <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>.</span></span> <span data-ttu-id="76153-122">當您載入或儲存控制項的設定時, 會將的值<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>傳遞<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>至<xref:System.Configuration.ApplicationSettingsBase>類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="76153-122">When you load or save the control's settings, you pass the value of <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> on to the <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> property of the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span> <span data-ttu-id="76153-123">應用程式設定會在將使用者的設定保存至 XML 時, 使用此唯一索引鍵。</span><span class="sxs-lookup"><span data-stu-id="76153-123">Application Settings uses this unique key when it persists the user's settings to XML.</span></span> <span data-ttu-id="76153-124">下列程式碼範例會示範`<userSettings>`區段如何尋找名為`CustomControl1`的自訂控制項實例, 以儲存其`Text`屬性的設定。</span><span class="sxs-lookup"><span data-stu-id="76153-124">The following code example shows how a `<userSettings>` section may look for an instance of a custom control named `CustomControl1` that saves a setting for its `Text` property.</span></span>

```xml
<userSettings>
    <CustomControl1>
        <setting name="Text" serializedAs="string">
            <value>Hello, World</value>
        </setting>
    </CustomControl1>
</userSettings>
```

 <span data-ttu-id="76153-125">未提供值的<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>控制項的任何實例都會共用相同的設定。</span><span class="sxs-lookup"><span data-stu-id="76153-125">Any instances of a control that do not supply a value for <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> will share the same settings.</span></span>

## <a name="see-also"></a><span data-ttu-id="76153-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76153-126">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [<span data-ttu-id="76153-127">應用程式設定架構</span><span class="sxs-lookup"><span data-stu-id="76153-127">Application Settings Architecture</span></span>](application-settings-architecture.md)
