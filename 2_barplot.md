## 1. barplot with error bars
```
#定义函数根据分组计算mean与sd
data_summary <- function(data, varname, groupnames){
  require(plyr)
  summary_func <- function(x, col){
    c(mean = mean(x[[col]], na.rm=TRUE),
      sd = sd(x[[col]], na.rm=TRUE))
  }
  data_sum<-ddply(data, groupnames, .fun=summary_func,
                  varname)
  return(data_sum)
}
df2 <- data_summary(df, varname="exp", 
                    groupnames=c("group"))
df2
df2$Group=as.factor(df2$group)
library(ggpubr)
ggplot(df2, aes(x=Group, y=mean, fill=Group)) + 
  geom_bar(stat="identity", color="white", position=position_dodge(), width = 0.8) +
  geom_errorbar(aes(ymin=mean-sd, ymax=mean+sd), width=.32,
                position=position_dodge(.9)) +
  scale_y_continuous(expand = c(0,0))+
  ylab('Expression level')+xlab('')+
  scale_fill_manual(values = c("#e7211a", "#ea5251", "#f08d8d",
                               "#f7d5d5", "#f7d5d5", "#f7d5d5"))+
  theme_default+theme(axis.text.x = element_text(colour="black",size=14, angle = 30, vjust = 0.6))
```
