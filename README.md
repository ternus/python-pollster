# pollster

A Python wrapper for the [Pollster API](http://elections.huffingtonpost.com/pollster/api) 
which provides access to political opinion polling data and trend estimates from The Huffington Post.

## Installation

    pip install pollster

## Getting started

    from pollster import Pollster
    pollster = Pollster()

See the current estimate of the president's job approval

    chart = pollster.charts(topic='obama-job-approval')[0]
    print chart.esimtates

List charts about 2012 Senate races

    pollster.charts(topic='2012-senate')

List charts about Wisconsin

    pollster.charts(state='WI')

Calculate the margin between Obama and Romney from a recent general election poll

    poll = pollster.polls(chart='2012-general-election-romney-vs-obama')[0]
    question = [x for x in poll.questions if x['chart'] == '2012-general-election-romney-vs-obama'][0]
    obama = [x for x in question['responses'] if x['choice'] == 'Obama'][0]
    romney = [x for x in question['responses'] if x['choice'] == 'Romney'][0]
    print obama['value'] - romney['value']

See the methodology used in recent polls about the Affordable Care Act

    chart = pollster.chart(slug='us-health-bill')
    print [[x.pollster, x.method] for x in chart.polls()]

## Authors

- Aaron Bycoffe, bycoffe@huffingtonpost.com

## Copyright

Copyright © 2012 The Huffington Post. See LICENSE for details.