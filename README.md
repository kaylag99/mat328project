# mat328project

##bar chart of num of crashes in each borough
borough_counts = crash["borough"].value_counts()
borough_counts.plot(kind = "bar")
plt.title("Number of Crashes by Borough")
plt.xlabel("Borough")
plt.ylabel("# of Crashes")

##hist of num ppl killed
crash["num_persons_killed"].hist(bins= 20)
plt.xlabel("People Killed")
plt.ylabel("frequency")
plt.title("Distribution of all People Killed in Crashes")

##hist of num ppl injured
crash["num_persons_injured"].hist(bins= 20)
plt.xlabel("People injured")
plt.ylabel("frequency")
plt.title("Distribution of all People Injured in Crashes")

##bar chart of num of crashes in each year: bars are in ascending order rather than by year
year_counts = crash["date"].value_counts()
year_counts.plot(kind = "bar")
plt.title("Number of Crashes by Year")
plt.xlabel("Year")
plt.ylabel("# of Crashes")

#line plot: injuries total by borough per year: why is the scale in the y axis less than 1?
sns.relplot(x = "date", y = "num_persons_injured", hue = "borough", kind = "line", data = crash, ci = None)
plt.title("Number of People Injured per Year by Borough")

#line plot: deaths total by borough per year; the scale on the y axis is not right
sns.relplot(x = "date", y = "num_persons_killed", hue = "borough", kind = "line", data = crash, ci = None)
plt.title("Number of People Killed per Year by Borough")
