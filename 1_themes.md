## theme
```
theme_default <- theme_pubr()+theme(legend.position = 'none',
   axis.text.x = element_text(colour="black",size=14),
   axis.text.y = element_text(colour="black",size=10),
   axis.ticks = element_line(colour="black", size = 0.75),
   axis.ticks.length = unit(.25, "cm"),
   axis.title=element_text(size=14),
   axis.line = element_line(colour="black", size = 0.75))
   
theme_with_box <- theme_pubr()+theme(legend.position = "none",
        axis.line = element_line(size = 0),
        panel.border = element_rect(linewidth = 1,fill=NA,color = 'Black'),
        plot.title = element_text(hjust = 0.5))+
          scale_x_discrete(labels= c('Male (n = 10)', 'Female (n = 13)'))
    
theme_umap <- theme(axis.line = element_blank(),
                        axis.ticks = element_blank(),
                        axis.text = element_blank(),
                        panel.border = element_rect(fill = NA,color = "black",
                        size=2,linetype = "solid"))+
                        xlab('UMAP1')+ylab('UMAP2')
```
