---
title: "Implementing the UI Automation RangeValue Control Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control patterns, Range Value"
  - "Range Value control pattern"
  - "UI Automation, Range Value control pattern"
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
caps.latest.revision: 19
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 19
---
# Implementing the UI Automation RangeValue Control Pattern
> [!NOTE]
>  이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](http://go.microsoft.com/fwlink/?LinkID=156746)를 참조하세요.  
  
 이 항목에서는 이벤트 및 속성에 대한 정보를 포함하여 <xref:System.Windows.Automation.Provider.IRangeValueProvider>를 구현하기 위한 지침 및 규칙을 제공합니다. 추가 참조에 대한 링크는 항목 끝에 나열되어 있습니다.  
  
 <xref:System.Windows.Automation.RangeValuePattern> 컨트롤 패턴은 범위 내의 값으로 설정할 수 있는 컨트롤을 지원하는 데 사용됩니다. 이 컨트롤 패턴을 구현하는 컨트롤의 예제를 보려면 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)을 참조하세요.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## 구현 지침 및 규칙  
 Range Value 컨트롤 패턴을 구현할 때는 다음 지침 및 규칙에 유의하세요.  
  
-   컨트롤을 통해 로캘 또는 사용자 기본 설정에 따라 지원되는 속성을 보정할 수 있습니다. 이러한 예로 온도가 화씨 또는 섭씨로 표시되도록 설정할 수 있는 온도계 컨트롤이 있습니다.  
  
-   진행률 표시줄 또는 슬라이더와 같은 모호한 범위 값이 있는 컨트롤에서는 해당 값을 정규화해야 합니다.  
  
 ![진행률 표시줄](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA\_RangeValuePattern\_Progress\_Bar")  
이 예로는 값이 정수 유형인 진행률 표시줄이며 최소 및 최대 속성 값이 각각 0과 100으로 정규화됩니다.  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## IRangeValueProvider에 필요한 멤버  
  
|필요한 멤버|멤버 형식|노트|  
|------------|-----------|--------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|속성|없음|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|속성|없음|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|속성|없음|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|속성|없음|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|속성|없음|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|속성|없음|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|메서드|없음|  
  
 이 컨트롤 패턴에 연결된 이벤트가 없습니다.  
  
<a name="Exceptions"></a>   
## 예외  
 공급자는 다음과 같은 예외를 throw해야 합니다.  
  
|예외 형식|조건|  
|-----------|--------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>은 <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> 보다 크거나 <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty> 보다 작은 값으로 호출됩니다.|  
  
## 참고 항목  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)