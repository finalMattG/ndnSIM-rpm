
Obtaining metrics
=================

To obtain simulation results, you would need to connect to one or more `trace sources <doxygen/group___trace_source_list.html>`_ provided by ndnSIM classes.


Tracer classes
--------------

ndnSIM provides a few helper tracers that simplify process of obtaining metrics.

Currently, there are only 2 useful tracers: 

- :ndnsim:`ndn::L3AggregateTracer`

    Tracing the aggregate number of Interests/Data packets forwarded by an NDN node 

    The following example enables tracing on all simulation nodes:

    .. code-block:: c++

        // the following should be put just before calling Simulator::Run in the scenario

        boost::tuple< boost::shared_ptr<std::ostream>, std::list<Ptr<L3AggregateTracer> > >
            tracers = L3RateTracer::InstallAll ("aggregate-trace.txt", Seconds (1.0));
        
        Simulator::Run ();


- :ndnsim:`ndn::L3RateTracer`

    Tracing the rate in bytes and in number of packets of Interest/Data packets forwarded by an NDN node 

    The following example enables tracing on all simulation nodes:

    .. code-block:: c++

        // the following should be put just before calling Simulator::Run in the scenario

        boost::tuple< boost::shared_ptr<std::ostream>, std::list<Ptr<L3RateTracer> > >
            tracers = L3RateTracer::InstallAll ("rate-trace.txt", Seconds (1.0));
        
        Simulator::Run ();


.. note::

    A number of other tracers are available in ``plugins/tracers-broken`` folder, but they do not yet work with the current code.
    Eventually, we will port most of them to the current code, but it is not our main priority at the moment and would really appreciate help with writing new tracers and porting the old ones. 

