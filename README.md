- 👋 Hi, I’m @saswatim3
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
saswatim3/saswatim3 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
hi @boyGirl currently i am using victory-native in myc current project, 

Please let me know how to show a toolTip constantly onClick on bar graph. I have tried this code

 <VictoryChart
        name={"emptyArea"}
        height={200}
        width={350}>
         <VictoryAxis
          label={yAxisLabelText}
          tickValues={yAxisValue}
          dependentAxis={true}
          fixLabelOverlap={true}
          style={{
            grid: gridStyle,
            axis: yAxisStyle,
            ticks: yTicks,
            tickLabels: { fontSize: 10, padding: 5 },
            axisLabel: { fontSize: 10, padding: 40, fontWeight: "bold" },
          }}
        />
        <VictoryAxis
          tickValues={daysArray}
          dependentAxis={false}
          style={{
            ticks: xTicks,
            tickLabels: xTickLabel,
          }}
        />
            name={"earnedBar"}
            cornerRadius={barRadius}
            data={dataEarnedNewValue}
            alignment={barAlignment}
            style={{ data: burnedBarStyle }}
            labels={({ datum }) =>
            datum.y
            }
            events={[
              {
                target: "data",
                eventHandlers: {
                  // no-op the default tooltip onMouseOver and onMouseOut event handlers
                  onTouchStart: () => {},
                  onTouchEnd: () => {},
                  // add an onClick handler
                  onClick: () => {
                    return [
                      {
                        // this mutation sets `active: false` on all labels
                        eventKey: "all",
                        target: "labels",
                        mutation: () => ({ active: false })
                      },
                      {
                        // next, the second mutation sets `active: true` on just the slice you clicked
                        // the eventKey is set to the element that originated the event if non is given
                        target: "labels",
                        mutation: () => ({ active: true })
                      }
                    ];
                  }
                }
              }
            ]}
            labelComponent={
              <VictoryTooltip
               
                angle={90}
                orientation={"right"}
                style={{
                  fontSize: "10",
                  strokeWidth: 0.1,
                  fill: "#FFFFFF",
                  touchAction: "none",
                }}
                flyoutStyle={{ fill: "#b61414", stroke: "#FFFFFF" }}
                pointerLength={15}
            />
            }
          />

          <VictoryLine
          name="targetLine"
          style={{
            data: targetLineStyle,
          }}
          y={() => goal}
        />
      </VictoryChart>
