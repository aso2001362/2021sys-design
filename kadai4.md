```uml
@startuml
start
:weather= 1;
if(weather == 0)then(true)
:「快晴です」;
if(weather == 1)then(true)
:「曇りです」;
if(weather == 2)then(true)
:「雨です」;
else
:「不明です」;
endif
end
@enduml
```
