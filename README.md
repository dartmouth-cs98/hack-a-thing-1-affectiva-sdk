# Hack-A-Thing Affectiva SDK

### What I made

I worked with the [Affectiva SDK](https://www.affectiva.com) to build different emotion-tracking web apps, one of which involved integrating a chart using [D3.js](https://d3js.org). The first changes the color of the screen based on your emotional expression, the second shows a pie chart of your emotional breakdown, and the third determines if you have an rbf in any given moment.

* Screen-Changer: This was my first iteration, and my main goal was to get the Affectiva SDK working. I used [this fiddle](https://jsfiddle.net/qu3Lvzpg/) heavily as an example and referenced Affectiva's [documentation](https://knowledge.affectiva.com/v3.3/docs/analyze-the-camera-stream-3) a lot. The biggest issues by far in this stage were getting the web app connected to the webcam and understanding the data format returned by the SDK, but once that worked the rest went fairly smoothly. The screen changes smoothly between different colors for six different emotions (red for anger and contempt, yellow for joy, blue for sadness, green for disgust, purple for fear and orange for surprise), and chooses the color to display based on the emotion with the greatest percentage returned.

* Pie Chart: This version of the app shows a pie chart breakdown of the emotions you are currently displaying using the same colors listed above. I used the d3 data visualization JavaScript library and followed [these tutorials](http://www.cagrimmett.com/til/2016/08/19/d3-pie-chart.html) to get the chart to flow smoothly from one set of data to the next. I also added a debouncer so the data would only update every fifty frames instead of once every frame to make the app less sensitive to minor expression changes. The messiest part of this section was integrating d3 and understanding its process of creating SVG charts.

* RBF Tester: The last iteration of this project didn't do anything new but was mostly for my own entertainment. It is very similar to the first version, but now if you look at the camera with your normal neutral faceit will tell you if you have an rbf. This decision is made by seeing if your sum total of contempt, anger, and disgust is greater than 60% of your resting expression. The answer is presented below the start/stop buttons in a simple yes/no fashion.

### Who did what (if you worked with someone else)

Nope, just me.

### What you learned

I learned that APIs and SDKs are never as simple as they claim to be, and working with poor documentation means a lot of frustration and internet deep-dives. I tried for a long time to get the Affectiva SDK to recognize more than one face because the site advertises it as being able to recognize over 20, and then I found a buried forum answer that said this capability is not yet supported in the JavaScript SDK. I also learned that libraries/SDKs/APIs are *awesome* because, even with the overhead required, they are super powerful and allow you to get a ton of complex functionality going very quickly.

### What didn’t work

I couldn't get the SDK to recognize more than one face, but that's because the JavaScript SDK doesn't allow that capability. The pie chart is also a bit buggy, sometimes you can see the background while the pie chart redraws. If I had more time I would like to make the decision-making for the screen changer and rbf decider more complicated by involving the valence meter that the Affectiva SDK provides, so the app only changes if the valence of the emotion is over a certain value.