# Before

* Release slides (newest version)
* Prepare fall-back steps (video + dirs)
* Deploy test app to azure

---

* Double check internet connection - speedtest.net
* Open conf vendor logo in browser to copy url
* Make sure docker-machine is running
* Prepare Azure portal
* Prepare Docker hub
* Prepare GoQr.me
* Login to docker hub
* Make sure Flux is not running
* Turn on *Presentation Mode* -> Windows Mobility Center  http://www.thewindowsclub.com/presentation-settings-in-windows-7
* Start timer

# DEMO

## Creating SAFE project

* Create dir
* `dotnet new -i SAFE.Template`
* `dotnet new SAFE --Fulma --Remoting`
* `code .`
* `build run`
* While the build is running, tell more about Fulma and Remoting, and about project structure

## Architecture

* Shared code - counter type + Fable.Remoting - not restful, but just fine for our case
* Server side - how init counter works, webpart
* Client side - all compiled to fable, elmish architecture explained

## Building form 

* model init update in App.fs
* Replace "SAFE Template" with "SAFE Demo"
* Replace safeComponents with "Score the talk"
* Remove safeComponents
* Add logo: Level.level -> Level.item -> Image.image -> img (imgSrc depending on context)
* (git history)
* define onInput wih JsInterop; add comment to model4
* add model to name
* place some text in input to show that HMR preserves state

## Client side debugging

* Console trace
* Redux-devtools (Time-travel debugger)
* React-devtools - is outlined on smileys

## Talking to server side 

* Submitting vote - disabling controls on Loading
* Adding protocol to Fable.Remoting
* Server refresh (dotnet watch)
* Firing request in Client side
* Displaying results

## Deploy

* script, but also F# with FAKE
* bundle - publish server, collect client
* start docker-machine
* build docker
* run in docker -  `docker run -d -p 8085:8085 --rm --name safe-demo-test -it theimowski/safe-demo`
* login to docker (do before demo)
* deploy to docker hub
* azure - create new web app for container
* map port 8085 to 80 `az webapp config appsettings set --resource-group safe-demo --name safe-demo --settings WEBSITES_PORT=8085`
* think of something to say when the contianer is warming up

---

Agenda :

* Brief intro
* Tech Stack
  * Suave.IO
  * (Azure)?
  * Fable
  * Elmish
  * React
  * Redux time travel debugger
  * Fulma (Bulma)
  * F#
* dotnet new SAFE 
* `build run` - while running, explain stuff

---

To show:

* Explain Elm-architecture
 
* HMR

* Console trace
* Redux-devtools (time travel debugger)
* React-devtools (for better UI debugging) ? - what fancy can you do with that?

---

* Server refresh
* Shared code
* Server-side + client-side validation
* Debugging server side?
* Web App for Containers (Docker) - do manually, not from template?

* Deploying to Docker Hub + Azure - takes time, spend it to show some slides
* http://goqr.me/
* 
* ?Azure Storage

To resolve:

* Displaying comments together with name

* Writing comment on mobile with autocorrect -strange things happen
* Leave out disabling inputs?

* Pin paket so that it does not get updated?
* Pin packages so that they do not get updated?

* Old version of docker installed "system root pool not available on Windows"
* Template - view in separate file?

* Warning: C:/Users/BRE44821/.nuget/packages/fulma/1.0.0-beta-005/fable/Elements/Heading.fs
C:/Users/BRE44821/.nuget/packages/fulma/1.0.0-beta-005/fable/Elements/Heading.fs(92,8): (92,9) warning FABLE: Looks like Fulma.Elements.Heading.p uses point-free style, this may create problems in runtime, please declare all arguments explicitly.
 @ ./App.fs 19:0-115
 @ ./Client.fsproj
 @ multi (webpack)-dev-server/client?http://localhost:8080 webpack/hot/dev-server ./Client.fsproj 
 --> https://github.com/MangelMaxime/Fulma/pull/83 
