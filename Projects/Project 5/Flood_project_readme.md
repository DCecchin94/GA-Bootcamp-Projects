# Project 5 - Overview

#### Done by Julien Saleh & Daniel Cecchin


# Goal of the project

Floods are always devasting to communites. It takes 3 to 4 days for state services to be able to deploy to those regions as they have to assess where the damage and flooding is the worst. With our project, we aimed to be able to determime if there was indeed a flood and if so, whether it was low or high flood. This would allow state services to determine where they needed to deploy quicker as they would be using live data instead of satellite images.

# Data Sources

1) https://drive.google.com/file/d/1NvTyhUsrFbL91E10EPm38IjoCg6E2c6q/view

2) https://archive.ics.uci.edu/ml/machine-learning-databases/00456/

3) https://github.com/cvjena/eu-flood-dataset

Collectively these 3 sources contain over 5000 pictures. We only went through 3000 of them due to time. 


# Gathering the Data

1034 High Flood, 758 Low flood, 1015 No Flood

This part was difficult as there was no "flood" dataset that was either freely available and/or fit our needs. To remedy the problem we created our own dataset by going through a collection of 3000 pictures manually. We then proceeded to sort roughly 1000 photos into 1 of 3 categories: No Flood, Low Flood and High Flood. No Flood consisted of roughly 500 photos of dry land, parks, cities, streets, etc and roughly 500 were misc photos bringing the total to 1015. Photos such as cats, memes, letters, people's face and otehr things that were not water nor land. As Twitter allows users to post anything, we did not want the model to somehow confuse a picture of a window and then labeling it as flood. 

The Low Flood category was the hardest for us to determine what to place inside it. This was because what is a low flood? Was it when the water is at our ankles or until the water passes your waist? Some areas would have houses half submerged underwater while the majority of the city was left untouched by any water at all. We had to come back to this multiple times because determined exactly what we both had to be looking for was extremely hard. We both had our interpretation of at what level we deemed something to be a low flood or high flood. We eventually came to a consensus. From coming through it a few times we were left with a total of 758 photos. 

The High Flood category was quite easy to determine. Within the picture, if all and/or majoirty of the homes, buildings, structures or trees were submerged it was deemed High Flood. This category ended up having 1034 total.

Overall we used just under 3000 photos at a total of 2807.

# Results

We ran two models to determine which we would be going with and the first to be tested was a greyscale model. While our pictures were full RGB pictures we wanted to determine which would perform better. At first the results we were getting were either at our baseline or below, which was 36.84%. It was noticed that No Flood and Low Flood were being confused between each other a lot. To fix this, we went back to our data source and went through the data with a finer comb. This part took some time as debating over the semantics of "what makes this picture a flood", "there is water but no one is in danger", "people are walking around through this" is never an easy task. Our problem of determining at what level was it a low or high flood came back up when the model was getting confused between the Low Flood and the No Flood category. In the No Flood category, we decieded to remove any photo that had water in a way that may make the computer "think" it was a High Flood by mistake. Such an example wold be just an open river. At first we thought this was something worth keeping to train the model but it turned out to negatively impact our results. After further cleaning our data in this manner we re-ran the model. This time we were able to acheive an accuracy score of 62% where we were only achieving 52%-54% prior. Considering our baseline was 36.84%, our ability to increase it by almost 100% is commendable. 

# Next Steps

While increasing our model's accuracy from it's original 36.84% all the way to 62% is a great accomplishment. We would like to strive for a model that performs even better! Since this is not detecting simple things such as if an email is spam or not but rather natural disasters. Accuracy into the 97%+ range would be where we would like to see this type of model. 

Getting to the realm of 97% or higher is not an easy task to do. Especially since humans already have trouble when determining flood depth with our own eyes. To help began its journey to that goal, it would need many more photos. Next, perhaps more categories instead of just the three: No Flood, Low Flood and High Flood. This will allow us to place those hard to determine pictures into a better home instead of just stuffing them into a category that it "kind of" fits into. Lastly, getting a model to run with coloured pictures would ultimately be better. Using a coloured image would make our data more rich and thus more complex. 


# Scaling Up 

Before we scale up, being able to run efficently on Twitter should be the first bench mark. Once the program is competent in what it does, scaling up would rather be the program being able to take in and give more detail. This would look like actual depth of the water based on other strucures within a picture. If it knows that a stop sign is suppose to be 7ft and the water is up to the "S", that would be a good indication to the model that the depth of water is around 5.5ft-6ft deep. Things like this would give the the authorites even more information when trying to assess damage within an area. If we are thinking what a perfected program would look like, it would be able to aggregate all the available pictures coming in and make a map essentially of least damaged to most damaged areas. This would be possible when gathering data from Twitter posts if those posts contained location information. Within a few hours, authoiries would have essentially a heatmap dropped on top of an actual map. Allowing them to see flood depth, survivors and whatever else that may be important at the time. 







