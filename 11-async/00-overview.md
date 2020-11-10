## Async (Stretch Goal)

There are certain times where we need to construct relationships between the front and the back end where data retrieval is more complex than simply making an API call and displaying the results. This is especially true when you are dealing with streams of data or several api calls that are depending on other calls. 

The RXJS library was designed to handle cases like this. RXJS can work with any front end, but is most commonly used with Angular. 

The following resources can help you understand how RXJS works, with some examples to show it in action: 

[GitHub repo of RXJS methods](https://github.com/Nmuta/rxjsStuff)

[PDF: RXJS Real world use cases](https://www.slideshare.net/ladyleet/rxjs-operators-real-world-use-cases-full-version)

[Learn RXJS website](https://www.learnrxjs.io/operators/)

#### Here are some examples of Real World situations that may require RXJS:

<table>
  <tr>
    <th> Front end </th>
    <th> Back end </th>
  </tr>
  <tr>
    <td> An Autocomplete field on a page that pulls names from a database based on what you're just typed in . This requires making a new call to the back end every time a "key up" event happens on the front end.  </th>
    <td> The back end needs to have an autocomplete microservice that takes in whatever was passed to it from the user and returns all matching items in the database. This will require some work seeding the database.  For example, if a user has typed in "An" , you may want to have name entries of Andy, Anderson, Andover, Anthony, Anna, Ann, Anwar, Anita, etc. </td>
  </tr>
   
  <tr>
    <td> A real time service that shows the current "in stock" inventory of various products.
    </td>
    <td> The back end could be either a web socket (preferred), or simply a microservice that fakes the behavior of a dynamic resources by using some sort of dummy generated data that is constantly changing on an interval or based on the current time of day. For example, the amount of any product could be constantly decreasing based on the number of seconds that have passed since 12:01 am that morning. If you "fake" the dynamic back end , you may have to do some sort of polling on the front end that makes an API call every 2 seconds to the back end instead of using web sockets.</td>
  </tr>
   
  <tr>
    <td> A real time sales ticker. Similar to the above example, you may have a situation where you want to create a real time ticker of sales from various stores as they arrive and a final total of all of the combined sales. 
    ( <i>hint: See RXJS's 'combine latest' method </i> ) 
      
    </td>
    <td> The back end would be simliar to the idea above. You would have to use either web sockets or polling. </td>
  </tr>
</table>

#### Assignment: incorporate some sort of async data processing into your app. 

### !challenge
* type: project
* id: AD7654DE-4B22-APIA-B677-TMO2P2PASYNC
* title: Async

##### !question
## URL of front end containing async data
URL of front end containing async data
##### !end-question

##### !placeholder
URL of front end containing async data
##### !end-placeholder

##### !explanation
Thank you for your submission! 😀
##### !end-explanation
### !end-challenge