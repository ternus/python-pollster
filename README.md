# pollster

A Python wrapper for the [Pollster API](http://elections.huffingtonpost.com/pollster/api) 
which provides access to political opinion polling data and trend estimates from The Huffington Post.

    from pollster import Pollster

    # instantiate
    pollster = Pollster()

    charts = pollster.charts(topic='obama-job-approval')
    chart = charts[0]
    print chart
    print chart.estimates_by_date()

    # access all charts
    charts = pollster.charts()
    for chart in charts:
        print chart

    # access charts for a specific topic
    charts = pollster.charts(topic='obama-job-approval')
    for chart in charts:
        print chart

    # access the polls for a chart
    chart = charts[0]
    print chart
    polls = chart.polls()
    for poll in polls:
        print poll

    # page through polls
    polls = chart.polls(page=2)
    for poll in polls:
        print poll

    poll = polls[0]
    print poll.questions
