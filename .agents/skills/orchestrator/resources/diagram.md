``` mermaid 
graph TD
O[Orchestre]
E[Explorer]
P[Planer]
CoderPro[Pro Coder]
CoderBasic[Basic Coder]
R[Reviewer]
Reporter[Reporter]

start((start)) -- request User--> O[Orchestre]
	subgraph stage 1:Exploration
	  O -- request Use --> E
    E -- contex --> O
	end    
	subgraph stage 2:Planing
		O -- contex --> P
		P -- plan --> O
  end
 subgraph stage 3: Coding Implementation
		O --plan --> ResolverCoder{is complex or a big change}
		ResolverCoder -- true --> CoderPro
		ResolverCoder -- false --> CoderBasic
		CoderPro & CoderBasic == CodeChanges ==> O
  end
	subgraph stage 4: Review
		O --codeChanges--> R
		R -- feddback--> O
		O -- fedback --> completed{isCompleted}
		completed== NO: feedback ==> CoderPro & CoderBasic
	end
	subgraph stage 5: Reporting
		completed--YES: Completed --> Reporter
	end 
	Reporter --> eend((End))
```