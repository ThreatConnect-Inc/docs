Delete Tasks
------------

The example below demonstrates how to delete a Task Resource from the ThreatConnect platform:

.. code-block:: python
    :emphasize-lines: 12-15,18-19

    # replace the line below with the standard, TC script heading described here:
    # https://docs.threatconnect.com/en/latest/python/quick_start.html#standard-script-heading
    ...

    tc = ThreatConnect(api_access_id, api_secret_key, api_default_org, api_base_url)

    # instantiate Tasks object
    tasks = tc.tasks()

    owner = 'Example Community'

    # create an empty Task
    task = tasks.add('', owner)
    # set the ID of the new Task to the ID of the Task you would like to delete
    task.set_id(123456)

    try:
        # delete the Task
        task.delete()
    except RuntimeError as e:
        print(e)
        sys.exit(1)

.. note:: In the prior example, no API calls are made until the ``delete()`` method is invoked.
