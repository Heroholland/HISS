# HISS
 HTTP Injection Server Side is the future of Java web devlopment with the ability to create and render modules directly into HTML.
### Best used in conjunction with JavaWebserver that I created.
## Dependencies
Common Lang -> StringUtils - https://commons.apache.org/proper/commons-lang/download_lang.cgi
## Credits
Me. (To be honest, it took me forever to figure out some of the logic for the Strings lmao cause I had to replace in an already created string.)
## How to use
### Implementation
Begin by simply dragging the .jar file into the classpath of your Eclipse Project.
To create the HISS object follow the code below.
```java
HISS h = new HISS();
```
### Methods
```java
Component createComponent(String html, String name) // RETURNS A COMPONENT WITH THE SPECIFIED HTML AND NAME.
```
```java
void setClosing(boolean closing) // SETS THE TAG FOR THE MODULES TO </tagname> rather than <tagname>.
```
```java
void addDefaultComponents() // ADDS THE DEFAULT BUILT-IN COMPONENTS OF <jquery> and <winbox> javascript.
```
```java
String renderHTML(String html) // RENDERS AND RETURN THE HTML WITH COMPONENTS.
```
```java
Component getComponentWithName(String name) // RETURNS THE COMPONENT FROM CREATED COMPONENTS WITH THE SPECIFIED NAME.
```
```java
List<Component> getComponents() // RETURNS THE CURRENT COMPONENTS LIST.
```
```java
void setComponentHtml(String name, String html) // ALLOWS YOU TO CHANGE THE HTML OF A REGISTERED COMPONENT.
```
### Example
**Please be aware that this example is using my JavaHTTPServer API.**
#### Main.java
```java
public static void main(String[] args) throws IOException {
 WebserverMain ws = new WebserverMain(9000);
 HISS h = new HISS();
 h.setClosing(true);
 h.addDefaultComponents();
 h.createComponent("<iframe width=\"" + 560*4 + "\" height=\"" + 315*4 + "\" src=\"https://www.youtube-nocookie.com/embed/hzJVP5b61IA\" title=\"YouTube video player\" frameborder=\"0\" allow=\"accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture\" allowfullscreen></iframe>", "biggiecheese"); // CREATES A YOUTUBE COMPONENT WITH BIGGIE CHEESE.
 public static void main(String[] args) throws IOException {
}
```
#### RootHandler.java
```java
@Override
 public void handle(HttpExchange he) throws IOException {
  WebserverMain ws = Main.ws;
  ws.sendResponse(he, Main.h.renderHTML("<html> <head> </head> <body> </jquery></biggiecheese> </body> </html>"));
 }
```
